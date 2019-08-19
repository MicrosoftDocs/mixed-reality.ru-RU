---
title: MR и Azure 308 — уведомления между устройствами
description: Пройдите этот курс, чтобы узнать, как реализовать центры уведомлений Azure, функции Azure и службу хранилища Azure и таблицы в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, уведомление, функции, таблицы, центры уведомлений, hololens, иммерсивное, VR
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694605"
---
>[!NOTE]
><span data-ttu-id="8d661-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8d661-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8d661-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="8d661-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8d661-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8d661-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8d661-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="8d661-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8d661-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8d661-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8d661-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="8d661-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="8d661-110">MR и Azure 308: Уведомления между устройствами</span><span class="sxs-lookup"><span data-stu-id="8d661-110">MR and Azure 308: Cross-device notifications</span></span>

![окончательный продукт — запуск](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="8d661-112">В этом курсе вы узнаете, как добавлять возможности концентраторов уведомлений в приложение смешанной реальности с помощью центров уведомлений Azure, таблиц Azure и функций Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="8d661-113">**Центры уведомлений Azure** — это служба Майкрософт, которая позволяет разработчикам отправлять целевые и персонализированные push-уведомления на любую платформу, работающую в облаке.</span><span class="sxs-lookup"><span data-stu-id="8d661-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="8d661-114">Это позволяет разработчикам взаимодействовать с конечными пользователями или даже взаимодействовать между различными приложениями в зависимости от сценария.</span><span class="sxs-lookup"><span data-stu-id="8d661-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="8d661-115">Дополнительные сведения см. на [странице](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)центров **уведомлений Azure** .</span><span class="sxs-lookup"><span data-stu-id="8d661-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="8d661-116">**Функции Azure** — это служба Майкрософт, которая позволяет разработчикам запускать небольшие фрагменты кода "функции" в Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="8d661-117">Это позволяет делегировать работу в облако, а не локальное приложение, которое может иметь множество преимуществ.</span><span class="sxs-lookup"><span data-stu-id="8d661-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="8d661-118">**Функции Azure** поддерживают несколько языков разработки, включая C\#, F\#, Node. js, Java и PHP.</span><span class="sxs-lookup"><span data-stu-id="8d661-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="8d661-119">Дополнительные сведения см. на [странице](https://docs.microsoft.com/azure/azure-functions/functions-overview) **функций Azure**.</span><span class="sxs-lookup"><span data-stu-id="8d661-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="8d661-120">**Таблицы Azure** — это облачная служба Майкрософт, которая позволяет разработчикам хранить структурированные данные, отличные от SQL, в облаке, что упрощает доступ к ним из любого места.</span><span class="sxs-lookup"><span data-stu-id="8d661-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="8d661-121">Служба может похвастаться структуру, которая обеспечивает развитие таблиц по мере необходимости, и, таким образом, является очень гибкой.</span><span class="sxs-lookup"><span data-stu-id="8d661-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="8d661-122">Дополнительные сведения см. на [странице](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) **таблиц Azure**</span><span class="sxs-lookup"><span data-stu-id="8d661-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="8d661-123">Прополнив этот курс, вы получите иммерсивное приложение для работы в смешанной реальности и приложение для настольного ПК, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="8d661-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="8d661-124">Приложение настольного ПК позволит пользователю перемещать объект в двухмерном пространстве (X и Y) с помощью мыши.</span><span class="sxs-lookup"><span data-stu-id="8d661-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="8d661-125">Перемещение объектов в приложении для ПК будет отправлено в облако с помощью JSON, которое будет иметь форму строки, содержащей идентификатор объекта, тип и сведения о преобразовании (координаты X и Y).</span><span class="sxs-lookup"><span data-stu-id="8d661-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="8d661-126">Приложение Mixed Reality, которое имеет идентичную сцену для классического приложения, будет получать уведомления о перемещении объектов из службы концентраторов уведомлений (которая только что была обновлена настольным приложением).</span><span class="sxs-lookup"><span data-stu-id="8d661-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="8d661-127">При получении уведомления, которое будет содержать идентификатор объекта, тип и сведения о преобразовании, приложение Mixed Reality применит полученные сведения к собственной сцене.</span><span class="sxs-lookup"><span data-stu-id="8d661-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="8d661-128">В приложении вы будете выполнять интеграцию результатов с вашей структурой.</span><span class="sxs-lookup"><span data-stu-id="8d661-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="8d661-129">Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="8d661-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="8d661-130">Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8d661-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="8d661-131">Этот курс является автономным учебником, который не участвует в других практических занятиях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8d661-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="8d661-132">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="8d661-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8d661-133">Хождение</span><span class="sxs-lookup"><span data-stu-id="8d661-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8d661-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8d661-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8d661-135"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="8d661-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="8d661-136">MR и Azure 308: Уведомления между устройствами</span><span class="sxs-lookup"><span data-stu-id="8d661-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="8d661-137">✔️</span><span class="sxs-lookup"><span data-stu-id="8d661-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8d661-138">✔️</span><span class="sxs-lookup"><span data-stu-id="8d661-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="8d661-139">Хотя этот курс в основном ориентирован на гарнитуры Windows Mixed Reality (VR), вы также можете применить сведения, которые вы узнаете в этом курсе, к Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8d661-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="8d661-140">Как вы пройдете вместе с курсом, вы увидите примечания о любых изменениях, которые могут потребоваться для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8d661-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="8d661-141">При использовании HoloLens вы можете заметить некоторые эхо во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="8d661-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d661-142">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="8d661-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="8d661-143">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="8d661-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="8d661-144">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018).</span><span class="sxs-lookup"><span data-stu-id="8d661-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="8d661-145">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.</span><span class="sxs-lookup"><span data-stu-id="8d661-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="8d661-146">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="8d661-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="8d661-147">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="8d661-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="8d661-148">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="8d661-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8d661-149">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="8d661-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8d661-150">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="8d661-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8d661-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8d661-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="8d661-152">Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="8d661-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="8d661-153">Доступ к Интернету для установки Azure и доступа к концентраторам уведомлений</span><span class="sxs-lookup"><span data-stu-id="8d661-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="8d661-154">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="8d661-154">Before you start</span></span>

- <span data-ttu-id="8d661-155">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="8d661-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="8d661-156">Вы должны быть владельцем портала разработчика Майкрософт и портала регистрации приложений, в противном случае у вас не будет разрешения на доступ к приложению в [главе 2](#chapter-2---retrieve-your-new-apps-credentials).</span><span class="sxs-lookup"><span data-stu-id="8d661-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="8d661-157">Глава 1. Создание приложения на портале разработчика Майкрософт</span><span class="sxs-lookup"><span data-stu-id="8d661-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="8d661-158">Чтобы использовать службу **концентраторов уведомлений Azure** , необходимо создать приложение на портале разработчика Майкрософт, так как приложение должно быть зарегистрировано, чтобы оно может отправлять и получать уведомления.</span><span class="sxs-lookup"><span data-stu-id="8d661-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="8d661-159">Войдите на [портал разработчика Майкрософт](https://developer.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="8d661-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="8d661-160">Вам потребуется войти в учетную запись Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8d661-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="8d661-161">На панели мониторинга щелкните **создать новое приложение**.</span><span class="sxs-lookup"><span data-stu-id="8d661-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Создание приложения](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="8d661-163">Появится всплывающее окно, где необходимо зарезервировать имя нового приложения.</span><span class="sxs-lookup"><span data-stu-id="8d661-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="8d661-164">В текстовое поле вставьте соответствующее имя. Если выбранное имя доступно, справа от текстового поля появится галочка.</span><span class="sxs-lookup"><span data-stu-id="8d661-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="8d661-165">После добавления доступного имени нажмите кнопку **резервное название продукта** в левом нижнем углу всплывающего окна.</span><span class="sxs-lookup"><span data-stu-id="8d661-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![обратить имя](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="8d661-167">Теперь, когда приложение создано, вы можете перейти к следующей главе.</span><span class="sxs-lookup"><span data-stu-id="8d661-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="8d661-168">Глава 2. получение учетных данных для новых приложений</span><span class="sxs-lookup"><span data-stu-id="8d661-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="8d661-169">Войдите на портал регистрации приложений, где будет указано новое приложение, и получите учетные данные, которые будут использоваться для настройки **службы концентраторов уведомлений** на **портале Azure**.</span><span class="sxs-lookup"><span data-stu-id="8d661-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="8d661-170">Перейдите на [портал регистрации приложений](http://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="8d661-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![Портал регистрации приложений](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="8d661-172">Для входа в систему необходимо использовать учетную запись Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8d661-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="8d661-173">Это **должна** быть учетная запись Майкрософт, которая использовалась в предыдущей [главе](#chapter-1---create-an-application-on-the-microsoft-developer-portal)с порталом для разработчиков Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="8d661-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="8d661-174">Приложение будет найдено в разделе **Мои приложения** .</span><span class="sxs-lookup"><span data-stu-id="8d661-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="8d661-175">Найдя его, щелкните его, и вы перейдете на новую страницу с именем приложения и **регистрацией**.</span><span class="sxs-lookup"><span data-stu-id="8d661-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![Ваше недавно зарегистрированное приложение](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="8d661-177">Прокрутите страницу регистрации вниз и найдите раздел **секреты приложения** и **идентификатор безопасности пакета** для приложения.</span><span class="sxs-lookup"><span data-stu-id="8d661-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="8d661-178">Скопируйте оба этих параметра для использования с настройкой **службы "центры уведомлений Azure** " в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="8d661-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![Секреты приложения](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="8d661-180">Глава 3. Настройка портала Azure: создание службы концентраторов уведомлений</span><span class="sxs-lookup"><span data-stu-id="8d661-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="8d661-181">После извлечения учетных данных приложения необходимо открыть портал Azure, где вы создадите службу центров уведомлений Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="8d661-182">Войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="8d661-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="8d661-183">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="8d661-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="8d661-184">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="8d661-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="8d661-185">Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу, а затем найдите **Центр уведомлений**и нажмите клавишу ***Ввод***.</span><span class="sxs-lookup"><span data-stu-id="8d661-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![Поиск центра уведомлений](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="8d661-187">Слово ***New*** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="8d661-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="8d661-188">На новой странице будет представлено описание службы *концентраторов уведомлений* .</span><span class="sxs-lookup"><span data-stu-id="8d661-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="8d661-189">В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="8d661-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Создание экземпляра концентраторов уведомлений](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="8d661-191">После нажатия кнопки ***создать***:</span><span class="sxs-lookup"><span data-stu-id="8d661-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="8d661-192">Вставьте нужное имя для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="8d661-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="8d661-193">Укажите **пространство имен** , которое вы сможете связать с этим приложением.</span><span class="sxs-lookup"><span data-stu-id="8d661-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="8d661-194">Выберите **расположение.**</span><span class="sxs-lookup"><span data-stu-id="8d661-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="8d661-195">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="8d661-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="8d661-196">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="8d661-197">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8d661-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="8d661-198">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="8d661-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="8d661-199">Выберите подходящую **подписку**.</span><span class="sxs-lookup"><span data-stu-id="8d661-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="8d661-200">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="8d661-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="8d661-201">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="8d661-201">Select **Create**.</span></span>

        ![Заполнение сведений о службе](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="8d661-203">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="8d661-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="8d661-204">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="8d661-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![уведомление](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="8d661-206">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="8d661-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="8d661-207">Вы будете перенаправлены на новый экземпляр службы **концентратора уведомлений** .</span><span class="sxs-lookup"><span data-stu-id="8d661-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![Переход к ресурсу](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="8d661-209">На странице Обзор в середине страницы щелкните **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="8d661-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="8d661-210">Панель справа изменится на отображение двух текстовых полей, требующих идентификатора безопасности и **ключа безопасности** **пакета** , из приложения, настроенного ранее.</span><span class="sxs-lookup"><span data-stu-id="8d661-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![вновь созданная служба концентраторов](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="8d661-212">После копирования сведений в правильные поля нажмите кнопку **сохранить**, и вы получите уведомление об успешном обновлении центра уведомлений.</span><span class="sxs-lookup"><span data-stu-id="8d661-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![Копировать сведения о безопасности](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="8d661-214">Глава 4. Настройка портала Azure: создание службы таблиц</span><span class="sxs-lookup"><span data-stu-id="8d661-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="8d661-215">После создания экземпляра службы концентраторов уведомлений вернитесь на портал Azure, где вы создадите службу таблиц Azure, создав ресурс хранилища.</span><span class="sxs-lookup"><span data-stu-id="8d661-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="8d661-216">Если вы еще не вошли в систему, войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="8d661-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="8d661-217">После входа в систему щелкните **создать** в левом верхнем углу и найдите **учетную запись хранения**и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="8d661-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="8d661-218">Слово ***New*** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="8d661-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="8d661-219">В списке выберите **учетная запись хранения — BLOB-объект, файл, таблица и очередь** .</span><span class="sxs-lookup"><span data-stu-id="8d661-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Поиск учетной записи хранения](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="8d661-221">На новой странице будет представлено описание службы **учетной записи хранения** .</span><span class="sxs-lookup"><span data-stu-id="8d661-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="8d661-222">В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="8d661-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="8d661-224">После нажатия кнопки **создать**появится панель:</span><span class="sxs-lookup"><span data-stu-id="8d661-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="8d661-225">Вставьте нужное **имя** для этого экземпляра службы (необходимо указать все символы в нижнем регистре).</span><span class="sxs-lookup"><span data-stu-id="8d661-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="8d661-226">В качестве **модели развертывания**щелкните **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="8d661-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="8d661-227">Для **типа учетной записи**в раскрывающемся меню выберите **хранилище (общее назначение v1)** .</span><span class="sxs-lookup"><span data-stu-id="8d661-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="8d661-228">Выберите подходящее **Расположение**.</span><span class="sxs-lookup"><span data-stu-id="8d661-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="8d661-229">В раскрывающемся меню репликация выберите **доступ для чтения — геоизбыточное хранилище (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="8d661-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="8d661-230">Для **повышения производительности**щелкните **стандартный**.</span><span class="sxs-lookup"><span data-stu-id="8d661-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="8d661-231">В разделе **Обязательное безопасное перемещение** выберите **отключено**.</span><span class="sxs-lookup"><span data-stu-id="8d661-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="8d661-232">В раскрывающемся меню **Подписка** выберите подходящую подписку.</span><span class="sxs-lookup"><span data-stu-id="8d661-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="8d661-233">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="8d661-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="8d661-234">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="8d661-235">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8d661-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="8d661-236">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="8d661-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="8d661-237">Оставьте **виртуальные сети** **отключенными** , если это возможно.</span><span class="sxs-lookup"><span data-stu-id="8d661-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="8d661-238">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="8d661-238">Click **Create**.</span></span>

        ![Заполнение сведений о хранилище](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="8d661-240">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="8d661-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="8d661-241">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="8d661-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="8d661-242">Щелкните уведомления, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="8d661-242">Click on the notifications to explore your new Service instance.</span></span>

    ![уведомление о новом хранилище](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="8d661-244">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="8d661-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="8d661-245">Будет выполнен переход на новую страницу обзора экземпляра службы хранилища.</span><span class="sxs-lookup"><span data-stu-id="8d661-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![Переход к ресурсу](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="8d661-247">На странице Обзор в правой части щелкните **таблицы**.</span><span class="sxs-lookup"><span data-stu-id="8d661-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="8d661-248">Панель справа изменится на отображение сведений о **службе таблиц** , где необходимо добавить новую таблицу.</span><span class="sxs-lookup"><span data-stu-id="8d661-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="8d661-249">Для этого нажмите **+** кнопку **Таблица** в левом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="8d661-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![Открытие таблиц](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="8d661-251">Будет отображена новая страница, где необходимо ввести **имя таблицы**.</span><span class="sxs-lookup"><span data-stu-id="8d661-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="8d661-252">Это имя, которое будет использоваться для ссылки на данные в приложении в последующих главах.</span><span class="sxs-lookup"><span data-stu-id="8d661-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="8d661-253">Вставьте соответствующее имя и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="8d661-253">Insert an appropriate name and click **OK**.</span></span>

    ![создать новую таблицу](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="8d661-255">После создания новой таблицы ее можно будет увидеть на странице **службы таблиц** (в нижней части).</span><span class="sxs-lookup"><span data-stu-id="8d661-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![создана новая таблица](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="8d661-257">Глава 5. Заполнение таблицы Azure в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8d661-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="8d661-258">Теперь, когда учетная запись хранения **службы таблиц** была настроена, можно добавить в нее данные, которые будут использоваться для хранения и извлечения информации.</span><span class="sxs-lookup"><span data-stu-id="8d661-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="8d661-259">Редактирование таблиц можно выполнить с помощью **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8d661-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="8d661-260">Откройте **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8d661-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="8d661-261">В меню щелкните **Просмотреть** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="8d661-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![открыть Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="8d661-263">**Cloud Explorer** откроется как закрепленный элемент (подождите, так как загрузка может занять некоторое время).</span><span class="sxs-lookup"><span data-stu-id="8d661-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="8d661-264">Если подписка, использованная для создания *учетных записей хранения* , не отображается, убедитесь, что у вас есть:</span><span class="sxs-lookup"><span data-stu-id="8d661-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="8d661-265">Войдите в ту же учетную запись, которая использовалась для портала Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="8d661-266">Выберите подписку на странице управления учетными записями (может потребоваться применить фильтр из параметров учетной записи):</span><span class="sxs-lookup"><span data-stu-id="8d661-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![Найти подписку](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="8d661-268">Будут показаны облачные службы Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="8d661-269">Найдите **учетные записи хранения** и щелкните стрелку слева от нее, чтобы развернуть учетные записи.</span><span class="sxs-lookup"><span data-stu-id="8d661-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Открытие учетных записей хранения](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="8d661-271">После развертывания вновь созданная **учетная запись хранения** должна быть доступна.</span><span class="sxs-lookup"><span data-stu-id="8d661-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="8d661-272">Щелкните стрелку слева от хранилища, а затем после разворачивания найдите **таблицы** и щелкните стрелку рядом с ней, чтобы открыть **таблицу** , созданную в последней главе.</span><span class="sxs-lookup"><span data-stu-id="8d661-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="8d661-273">Дважды щелкните **таблицу**.</span><span class="sxs-lookup"><span data-stu-id="8d661-273">Double click your **Table**.</span></span>

    ![открыть таблицу объектов сцены](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="8d661-275">Таблица откроется в центре окна Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d661-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="8d661-276">Щелкните значок таблицы с рядом с **+** ним (плюс).</span><span class="sxs-lookup"><span data-stu-id="8d661-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![Добавить новую таблицу](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="8d661-278">Появится окно с запросом на *Добавление сущности*.</span><span class="sxs-lookup"><span data-stu-id="8d661-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="8d661-279">В итоге вы создадите три сущности, каждая из которых имеет несколько свойств.</span><span class="sxs-lookup"><span data-stu-id="8d661-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="8d661-280">Вы увидите, что *PartitionKey* и *RowKey* уже предоставлены, так как они используются таблицей для поиска данных.</span><span class="sxs-lookup"><span data-stu-id="8d661-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![ключ секции и строки](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="8d661-282">Обновите *значение* **PartitionKey** и **RowKey** следующим образом (не забудьте сделать это для каждого добавляемого свойства строки, хотя каждый раз следует увеличивать RowKey):</span><span class="sxs-lookup"><span data-stu-id="8d661-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![добавить правильные значения](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="8d661-284">Нажмите кнопку **Добавить свойство** , чтобы добавить дополнительные строки данных.</span><span class="sxs-lookup"><span data-stu-id="8d661-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="8d661-285">Создайте первую пустую таблицу, совпадающую с таблицей ниже.</span><span class="sxs-lookup"><span data-stu-id="8d661-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="8d661-286">По завершении нажмите кнопку **ОК** .</span><span class="sxs-lookup"><span data-stu-id="8d661-286">Click **OK** when you are finished.</span></span>

    ![по завершении нажмите кнопку ОК.](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="8d661-288">Убедитесь, что вы изменили **тип** **X**, **Y**и **Z**, записи на **Double**.</span><span class="sxs-lookup"><span data-stu-id="8d661-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="8d661-289">Обратите внимание, что таблица теперь содержит строку данных.</span><span class="sxs-lookup"><span data-stu-id="8d661-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="8d661-290">Еще раз щелкните значок **(плюс),чтобыдобавитьдругуюсущность.+**</span><span class="sxs-lookup"><span data-stu-id="8d661-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![Первая строка](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="8d661-292">Создайте дополнительное свойство, а затем задайте значения для новой сущности в соответствии с показанными ниже.</span><span class="sxs-lookup"><span data-stu-id="8d661-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![Добавить куб](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="8d661-294">Повторите Последнее действие, чтобы добавить другую сущность.</span><span class="sxs-lookup"><span data-stu-id="8d661-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="8d661-295">Задайте значения для этой сущности, указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="8d661-295">Set the values for this entity to those shown below.</span></span>

    ![добавить цилиндр](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="8d661-297">Теперь таблица должна выглядеть так, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="8d661-297">Your table should now look like the one below.</span></span>

    ![Таблица завершена](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="8d661-299">Вы выполнили эту главу.</span><span class="sxs-lookup"><span data-stu-id="8d661-299">You have completed this Chapter.</span></span> <span data-ttu-id="8d661-300">Обязательно сохраните.</span><span class="sxs-lookup"><span data-stu-id="8d661-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="8d661-301">Глава 6. Создание приложение-функция Azure</span><span class="sxs-lookup"><span data-stu-id="8d661-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="8d661-302">Создайте приложение-функция Azure, который будет вызываться настольным приложением для обновления службы **таблиц** и отправки уведомления через **Центр уведомлений**.</span><span class="sxs-lookup"><span data-stu-id="8d661-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="8d661-303">Сначала необходимо создать файл, который позволит вашей функции Azure загружать нужные библиотеки.</span><span class="sxs-lookup"><span data-stu-id="8d661-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="8d661-304">Откройте **Блокнот** (нажмите клавишу Windows и введите Блокнот).</span><span class="sxs-lookup"><span data-stu-id="8d661-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![открыть Блокнот](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="8d661-306">При открытии блокнота вставьте в него структуру JSON.</span><span class="sxs-lookup"><span data-stu-id="8d661-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="8d661-307">После этого сохраните его на рабочем столе как **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="8d661-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="8d661-308">Важно, чтобы имя было правильным: Убедитесь, что оно **не имеет расширения txt** .</span><span class="sxs-lookup"><span data-stu-id="8d661-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="8d661-309">Этот файл определяет библиотеки, которые будет использовать функция. Если вы использовали NuGet, он покажется вам знакомым.</span><span class="sxs-lookup"><span data-stu-id="8d661-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

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

3.  <span data-ttu-id="8d661-310">Войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="8d661-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="8d661-311">Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу и выполните поиск по **приложение-функция**нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="8d661-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![Поиск приложения функции](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="8d661-313">Слово **New** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="8d661-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="8d661-314">На новой странице будет представлено описание службы **приложение-функция** .</span><span class="sxs-lookup"><span data-stu-id="8d661-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="8d661-315">В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="8d661-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![экземпляр приложения функции](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="8d661-317">После нажатия кнопки **создать**заполните следующие поля:</span><span class="sxs-lookup"><span data-stu-id="8d661-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="8d661-318">В качестве **имени приложения**вставьте нужное имя для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="8d661-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="8d661-319">Выберите **подписку**.</span><span class="sxs-lookup"><span data-stu-id="8d661-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="8d661-320">Выберите ценовую категорию, подходящую для вас. Если вы впервые создаете **службу приложение-функция**, вам будет доступен бесплатный уровень.</span><span class="sxs-lookup"><span data-stu-id="8d661-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="8d661-321">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="8d661-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="8d661-322">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="8d661-323">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8d661-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="8d661-324">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="8d661-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="8d661-325">Для **ОС**щелкните Windows, так как это Целевая платформа.</span><span class="sxs-lookup"><span data-stu-id="8d661-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="8d661-326">Выберите **план размещения** (в этом учебнике используется **план потребления**).</span><span class="sxs-lookup"><span data-stu-id="8d661-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="8d661-327">Выберите **Расположение** **(выберите то же расположение, что и хранилище, созданное на предыдущем шаге)** .</span><span class="sxs-lookup"><span data-stu-id="8d661-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="8d661-328">В разделе **хранилище** **необходимо выбрать службу хранилища, созданную на предыдущем шаге**.</span><span class="sxs-lookup"><span data-stu-id="8d661-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="8d661-329">Вам не потребуется *Application Insights* в этом приложении, поэтому вы можете **оставить его без**изменений.</span><span class="sxs-lookup"><span data-stu-id="8d661-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="8d661-330">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="8d661-330">Click **Create**.</span></span>

        ![создать новый экземпляр](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="8d661-332">После нажатия кнопки **создать** необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="8d661-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="8d661-333">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="8d661-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![новое уведомление](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="8d661-335">Щелкните уведомления, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="8d661-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="8d661-336">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="8d661-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Переход к ресурсу](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="8d661-338">Щелкните значок(плюс) рядом с пунктом функции, чтобы *создать новый.* **+**</span><span class="sxs-lookup"><span data-stu-id="8d661-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![Добавить новую функцию](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="8d661-340">На центральной панели появится окно создания **функции** .</span><span class="sxs-lookup"><span data-stu-id="8d661-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="8d661-341">Проигнорируйте информацию в верхней половине панели и щелкните **Пользовательская функция**, расположенная рядом с нижней областью (в синей области, как показано ниже).</span><span class="sxs-lookup"><span data-stu-id="8d661-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="8d661-343">На новой странице в окне будут показаны различные типы функций.</span><span class="sxs-lookup"><span data-stu-id="8d661-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="8d661-344">Прокрутите вниз, чтобы просмотреть сиреневые типы, и щелкните **http-элемент размещения** .</span><span class="sxs-lookup"><span data-stu-id="8d661-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![Ссылка HTTP на размещение](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="8d661-346">Возможно, потребуется прокрутить страницу вниз (и этот образ может выглядеть неточно так же, если обновления на портале Azure выполнены), но вы ищете элемент, именуемый *http-* постановкой.</span><span class="sxs-lookup"><span data-stu-id="8d661-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="8d661-347">Откроется окно **http-размещения** , в котором необходимо настроить функцию (см. рисунок ниже для изображения).</span><span class="sxs-lookup"><span data-stu-id="8d661-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="8d661-348">Для **языка** в раскрывающемся меню выберите C\#.</span><span class="sxs-lookup"><span data-stu-id="8d661-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="8d661-349">В качестве **имени** введите соответствующее имя.</span><span class="sxs-lookup"><span data-stu-id="8d661-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="8d661-350">В раскрывающемся меню **уровень проверки** подлинности выберите **функция**.</span><span class="sxs-lookup"><span data-stu-id="8d661-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="8d661-351">В разделе **имя таблицы** необходимо указать точное имя, которое использовалось для создания службы **таблиц** ранее (включая тот же регистр букв).</span><span class="sxs-lookup"><span data-stu-id="8d661-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="8d661-352">В разделе **Подключение к учетной записи хранения** используйте раскрывающееся меню и выберите в нем свою учетную запись хранения.</span><span class="sxs-lookup"><span data-stu-id="8d661-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="8d661-353">Если это не так, щелкните **новую** гиперссылку рядом с заголовком раздела, чтобы отобразить другую панель, в которой должна быть указана учетная запись хранения.</span><span class="sxs-lookup"><span data-stu-id="8d661-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![новое хранилище](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="8d661-355">Нажмите кнопку **создать** , и вы получите уведомление о том, что параметры успешно обновлены.</span><span class="sxs-lookup"><span data-stu-id="8d661-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![Создание функции](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="8d661-357">После нажатия кнопки **создать**вы будете перенаправлены в редактор функций.</span><span class="sxs-lookup"><span data-stu-id="8d661-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![Обновление кода функции](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="8d661-359">Вставьте следующий код в редактор функций (заменив Код в функции):</span><span class="sxs-lookup"><span data-stu-id="8d661-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

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
    > <span data-ttu-id="8d661-360">Используя встроенные библиотеки, функция получает имя и расположение объекта, который был перемещен в сцене Unity (как C# объект, именуемый **унитигамеобжект**).</span><span class="sxs-lookup"><span data-stu-id="8d661-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="8d661-361">Затем этот объект используется для обновления параметров объекта в созданной таблице.</span><span class="sxs-lookup"><span data-stu-id="8d661-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="8d661-362">После этого функция вызывает созданную службу концентратора уведомлений, которая уведомляет все подписанные приложения.</span><span class="sxs-lookup"><span data-stu-id="8d661-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="8d661-363">После ввода кода нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="8d661-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="8d661-364">Затем щелкните **\<** значок (стрелка) в правой части страницы.</span><span class="sxs-lookup"><span data-stu-id="8d661-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![открыть панель отправки](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="8d661-366">Панель будет продвигаться справа.</span><span class="sxs-lookup"><span data-stu-id="8d661-366">A panel will slide in from the right.</span></span> <span data-ttu-id="8d661-367">На этой панели нажмите кнопку **Отправить**и отобразится обозреватель файлов.</span><span class="sxs-lookup"><span data-stu-id="8d661-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="8d661-368">Перейдите к и щелкните файл **Project. JSON** , созданный ранее в блокноте, а затем нажмите кнопку **Открыть** .</span><span class="sxs-lookup"><span data-stu-id="8d661-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="8d661-369">Этот файл определяет библиотеки, которые будет использовать функция.</span><span class="sxs-lookup"><span data-stu-id="8d661-369">This file defines the libraries that your function will use.</span></span>

    ![Отправить JSON](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="8d661-371">После отправки файл появится на панели справа.</span><span class="sxs-lookup"><span data-stu-id="8d661-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="8d661-372">Щелкнув его, вы откроете его в редакторе **функций** .</span><span class="sxs-lookup"><span data-stu-id="8d661-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="8d661-373">Он должен выглядеть **точно** так же, как и следующий образ (под шагом 23).</span><span class="sxs-lookup"><span data-stu-id="8d661-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="8d661-374">Затем на панели слева под элементом **функции**щелкните ссылку **Интеграция** .</span><span class="sxs-lookup"><span data-stu-id="8d661-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![Функция интеграции](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="8d661-376">На следующей странице в правом верхнем углу щелкните **Расширенный редактор** (как показано ниже).</span><span class="sxs-lookup"><span data-stu-id="8d661-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![откройте расширенный редактор](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="8d661-378">В центральной панели откроется файл **Function. JSON** , который необходимо заменить на следующий фрагмент кода.</span><span class="sxs-lookup"><span data-stu-id="8d661-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="8d661-379">Это определяет создаваемую функцию и параметры, передаваемые в функцию.</span><span class="sxs-lookup"><span data-stu-id="8d661-379">This defines the function you are building and the parameters passed into the function.</span></span>

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

26. <span data-ttu-id="8d661-380">Теперь редактор должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="8d661-380">Your editor should now look like the image below:</span></span>

    ![вернуться к стандартному редактору](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="8d661-382">Вы можете заметить, что только что вставленные входные параметры могут не соответствовать таблице и сведениям о хранилище, поэтому их необходимо обновить.</span><span class="sxs-lookup"><span data-stu-id="8d661-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="8d661-383">**Не выведем это**, как описано далее.</span><span class="sxs-lookup"><span data-stu-id="8d661-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="8d661-384">Просто щелкните ссылку **стандартный редактор** в правом верхнем углу страницы, чтобы вернуться назад.</span><span class="sxs-lookup"><span data-stu-id="8d661-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="8d661-385">Вернувшись в **стандартный редактор**, в разделе **входные данные**выберите **хранилище таблиц Azure (таблица)** .</span><span class="sxs-lookup"><span data-stu-id="8d661-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Входные данные таблицы](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="8d661-387">Убедитесь в следующем совпадении со **своими** сведениями, так как они могут отличаться (ниже приведены действия).</span><span class="sxs-lookup"><span data-stu-id="8d661-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="8d661-388">**Имя таблицы**: имя таблицы, созданной в службе "хранилище Azure" службы "таблицы".</span><span class="sxs-lookup"><span data-stu-id="8d661-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="8d661-389">**Подключение к учетной записи хранения.** щелкните **создать**, которое отображается рядом с раскрывающимся меню, и в правой части окна появится панель.</span><span class="sxs-lookup"><span data-stu-id="8d661-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![новое хранилище](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="8d661-391">Выберите **учетную запись хранения**, созданную ранее для размещения **приложений функций.**</span><span class="sxs-lookup"><span data-stu-id="8d661-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="8d661-392">Вы увидите, что значение подключения **учетной записи хранения** было создано.</span><span class="sxs-lookup"><span data-stu-id="8d661-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="8d661-393">По завершении нажмите кнопку **сохранить** .</span><span class="sxs-lookup"><span data-stu-id="8d661-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="8d661-394">Страница **входных данных** теперь должна соответствовать приведенной ниже странице, в **которой отображаются сведения** .</span><span class="sxs-lookup"><span data-stu-id="8d661-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![входные данные завершены](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="8d661-396">Затем в разделе **выходные данные**щелкните **Центр уведомлений Azure (уведомление)** .</span><span class="sxs-lookup"><span data-stu-id="8d661-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="8d661-397">Убедитесь, что следующие данные соответствуют **вашим** сведениям, так как они могут отличаться (ниже приведены действия).</span><span class="sxs-lookup"><span data-stu-id="8d661-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="8d661-398">**Имя концентратора уведомлений**. это имя созданного ранее экземпляра службы **концентратора уведомлений** .</span><span class="sxs-lookup"><span data-stu-id="8d661-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="8d661-399">**Подключение к пространству имен концентраторов уведомлений**: щелкните **создать**, которое отображается рядом с раскрывающимся меню.</span><span class="sxs-lookup"><span data-stu-id="8d661-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![проверить выходные данные](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="8d661-401">Появится всплывающее окно **подключения** (см. рисунок ниже), где необходимо выбрать **пространство имен** **концентратора уведомлений**, настроенного ранее.</span><span class="sxs-lookup"><span data-stu-id="8d661-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="8d661-402">Выберите имя **центра уведомлений** в среднем раскрывающемся меню.</span><span class="sxs-lookup"><span data-stu-id="8d661-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="8d661-403">Задайте для раскрывающегося меню **политики** значение **DefaultFullSharedAccessSignature**.</span><span class="sxs-lookup"><span data-stu-id="8d661-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="8d661-404">Нажмите кнопку **выбрать** , чтобы вернуться назад.</span><span class="sxs-lookup"><span data-stu-id="8d661-404">Click the **Select** button to go back.</span></span>

        ![Выходное обновление](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="8d661-406">Теперь страница **выходные данные** должна соответствовать приведенной ниже таблице, но вместо нее.</span><span class="sxs-lookup"><span data-stu-id="8d661-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="8d661-407">Обязательно нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="8d661-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="8d661-408">*Не изменяйте имя центра уведомлений напрямую* (все это должно быть выполнено с помощью **Расширенный редактор**, если выполнены предыдущие шаги правильно.</span><span class="sxs-lookup"><span data-stu-id="8d661-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![выходные данные завершены](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="8d661-410">На этом этапе необходимо протестировать функцию, чтобы убедиться, что она работает.</span><span class="sxs-lookup"><span data-stu-id="8d661-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="8d661-411">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-411">To do this:</span></span> 

    1. <span data-ttu-id="8d661-412">Еще раз перейдите на страницу функции:</span><span class="sxs-lookup"><span data-stu-id="8d661-412">Navigate to the function page once more:</span></span>

        ![выходные данные завершены](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="8d661-414">Вернитесь на страницу функция, щелкните вкладку **Test (тест** ) в правой части страницы, чтобы открыть колонку Test ( *тест* ):</span><span class="sxs-lookup"><span data-stu-id="8d661-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![выходные данные завершены](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="8d661-416">В текстовое поле **текст запроса** в колонке вставьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="8d661-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

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

    4. <span data-ttu-id="8d661-417">Выполнив тестовый код, нажмите кнопку **выполнить** в правом нижнем углу, и тест будет выполнен.</span><span class="sxs-lookup"><span data-stu-id="8d661-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="8d661-418">Выходные журналы теста будут отображаться в области консоли под кодом функции.</span><span class="sxs-lookup"><span data-stu-id="8d661-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![выходные данные завершены](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="8d661-420">Если приведенный выше тест завершается неудачно, необходимо проверить, что вы выполнили описанные выше действия точно, особенно параметры на **панели интеграции**.</span><span class="sxs-lookup"><span data-stu-id="8d661-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="8d661-421">Глава 7. Настройка проекта Unity для настольных систем</span><span class="sxs-lookup"><span data-stu-id="8d661-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d661-422">Настольное приложение, которое сейчас создается, **не будет** работать в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="8d661-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="8d661-423">Он должен выполняться вне редактора, после создания приложения с помощью Visual Studio (или развернутого приложения).</span><span class="sxs-lookup"><span data-stu-id="8d661-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="8d661-424">Ниже приведена типичная Настройка для разработки с помощью Unity и смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="8d661-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="8d661-425">Настройка и тестирование иммерсивного наушников смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8d661-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="8d661-426">Для этого курса **не** потребуется использовать контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="8d661-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="8d661-427">Если вам нужна поддержка настройки иммерсивного гарнитуры, перейдите по этой ссылке, [чтобы настроить Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="8d661-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="8d661-428">Откройте **Unity** и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="8d661-428">Open **Unity** and click **New**.</span></span>

    ![новый проект Unity](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="8d661-430">Необходимо указать имя проекта Unity, вставить **унитидесктопнотифхуб**.</span><span class="sxs-lookup"><span data-stu-id="8d661-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="8d661-431">Убедитесь, что для типа проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="8d661-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="8d661-432">Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="8d661-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="8d661-433">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="8d661-433">Then, click **Create project**.</span></span>

    ![создать проект](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="8d661-435">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8d661-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="8d661-436">Перейдите к разделу **изменение** > **настроек** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="8d661-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="8d661-437">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="8d661-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="8d661-438">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="8d661-438">Close the **Preferences** window.</span></span>

    ![Настройка внешних средств VS](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="8d661-440">Затем перейдите в раздел**параметры сборки** **файлов** > и выберите **универсальная платформа Windows**, а затем нажмите кнопку **переключения платформы** , чтобы применить выбранные элементы.</span><span class="sxs-lookup"><span data-stu-id="8d661-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Переключение платформ](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="8d661-442">Несмотря на то, что все еще находятся в**параметрах сборки** **файлов** > , убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="8d661-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="8d661-443">**Целевое устройство** настроено для **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="8d661-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="8d661-444">Это приложение будет использоваться для вашего рабочего стола, поэтому должно быть **любым устройством** .</span><span class="sxs-lookup"><span data-stu-id="8d661-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="8d661-445">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="8d661-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="8d661-446">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="8d661-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="8d661-447">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="8d661-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="8d661-448">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="8d661-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="8d661-449">Здесь стоит сохранить сцену и добавить ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="8d661-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="8d661-450">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="8d661-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="8d661-451">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="8d661-451">A save window will appear.</span></span>

            ![Добавление открытых сцен](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="8d661-453">Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="8d661-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Новая папка сцен](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="8d661-455">Откройте только что созданную папку **сцены** , а затем в поле **имя файла:** введите **\_NH Desktop\_сцены**и нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="8d661-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![создать NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="8d661-457">Оставшиеся параметры, в **параметрах сборки**, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8d661-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="8d661-458">В том же окне нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится **инспектор** .</span><span class="sxs-lookup"><span data-stu-id="8d661-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="8d661-459">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="8d661-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="8d661-460">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="8d661-461">Должна быть экспериментальная **версия среды выполнения сценариев** **(эквивалент .NET 4,6)**</span><span class="sxs-lookup"><span data-stu-id="8d661-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="8d661-462">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="8d661-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="8d661-463">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="8d661-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![4,6 NET version](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="8d661-465">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="8d661-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="8d661-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="8d661-466">**InternetClient**</span></span>

            ![Клиент Tick Internet](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="8d661-468">Назад в **параметрах сборки** *проекты\# Unity C* больше не заключаются; установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="8d661-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="8d661-469">Закройте окно **параметры сборки** .</span><span class="sxs-lookup"><span data-stu-id="8d661-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="8d661-470">Сохраните сцену и **файл** > проекта**сохранить сцену/файл** > **сохранить проект**.</span><span class="sxs-lookup"><span data-stu-id="8d661-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8d661-471">Если вы хотите пропустить компонент *настройки Unity* для этого проекта (классическое приложение) и продолжить работу с кодом, можно [скачать этот файл. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), импортировать его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [раздела 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="8d661-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="8d661-472">Все равно потребуется добавить компоненты скрипта.</span><span class="sxs-lookup"><span data-stu-id="8d661-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="8d661-473">Глава 8. импорт библиотек DLL в Unity</span><span class="sxs-lookup"><span data-stu-id="8d661-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="8d661-474">Вы будете использовать службу хранилища Azure для Unity (которая самостоятельно использует пакет SDK для .NET для Azure).</span><span class="sxs-lookup"><span data-stu-id="8d661-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="8d661-475">Дополнительные сведения см. по этой [ссылке о службе хранилища Azure для Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="8d661-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="8d661-476">В Unity существует известная ошибка, которая требует перенастройки подключаемых модулей после импорта.</span><span class="sxs-lookup"><span data-stu-id="8d661-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="8d661-477">Эти действия (4-7 в этом разделе) больше не понадобятся после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="8d661-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="8d661-478">Чтобы импортировать пакет SDK в собственный проект, убедитесь, что вы скачали последнюю версию [ **. пакет unitypackage**](https://aka.ms/azstorage-unitysdk) с сайта GitHub.</span><span class="sxs-lookup"><span data-stu-id="8d661-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="8d661-479">Затем выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-479">Then, do the following:</span></span>

1.  <span data-ttu-id="8d661-480">Добавьте **. пакет unitypackage** в Unity с помощью команды меню  **\> \> настраиваемый пакет импорт активов** .</span><span class="sxs-lookup"><span data-stu-id="8d661-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="8d661-481">В появившемся окне **Импорт пакета Unity** можно выбрать все в разделе \* \**подключаемый модуль* \> \* хранилище \* \* \*.</span><span class="sxs-lookup"><span data-stu-id="8d661-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="8d661-482">Снимите флажок все остальное, так как он не требуется для этого курса.</span><span class="sxs-lookup"><span data-stu-id="8d661-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Импорт в пакет](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="8d661-484">Нажмите кнопку ***Импорт*** , чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="8d661-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="8d661-485">Перейдите в папку **хранилища** подключаемых **модулей** в представлении проекта и выберите *только*следующие подключаемые модули:</span><span class="sxs-lookup"><span data-stu-id="8d661-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="8d661-486">Microsoft. Data. EDM</span><span class="sxs-lookup"><span data-stu-id="8d661-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="8d661-487">Microsoft. Data. OData</span><span class="sxs-lookup"><span data-stu-id="8d661-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="8d661-488">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="8d661-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="8d661-489">Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="8d661-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="8d661-490">System. пространственные</span><span class="sxs-lookup"><span data-stu-id="8d661-490">System.Spatial</span></span>

![снять флажок с любой платформы](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="8d661-492">Выбрав *нужные подключаемые модули* , **снимите флажок для** **любой платформы** и **снимите флажок** **всаплайер** , а затем нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="8d661-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![применение библиотек DLL платформы](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="8d661-494">Мы помечаем эти отдельные подключаемые модули для использования только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="8d661-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="8d661-495">Это связано с тем, что в папке WSA существуют разные версии тех же подключаемых модулей, которые будут использоваться после экспорта проекта из Unity.</span><span class="sxs-lookup"><span data-stu-id="8d661-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="8d661-496">В папке подключаемый модуль **хранилища** выберите только:</span><span class="sxs-lookup"><span data-stu-id="8d661-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="8d661-497">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="8d661-497">Microsoft.Data.Services.Client</span></span>

        ![Set не обрабатывать библиотеки DLL](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="8d661-499">Установите флажок **не обрабатывать** в разделе **параметры платформы** и нажмите кнопку ***Применить***.</span><span class="sxs-lookup"><span data-stu-id="8d661-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![не применять обработку](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="8d661-501">Мы помечаем этот подключаемый модуль "не обрабатывать", так как при обработке этого подключаемого модуля в установщике сборок Unity возникли трудности.</span><span class="sxs-lookup"><span data-stu-id="8d661-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="8d661-502">Подключаемый модуль по-прежнему будет работать, даже если он не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="8d661-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="8d661-503">Глава 9. Создание класса Таблетосцене в проекте Unity для настольных систем</span><span class="sxs-lookup"><span data-stu-id="8d661-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="8d661-504">Теперь необходимо создать скрипты, содержащие код для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="8d661-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="8d661-505">Первый скрипт, который необходимо создать, — это **таблетосцене**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="8d661-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="8d661-506">Чтение сущностей в таблице Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="8d661-507">С помощью табличных данных определите, какие объекты следует порождать и в какой должности.</span><span class="sxs-lookup"><span data-stu-id="8d661-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="8d661-508">Второй сценарий, который необходимо создать, — это **клаудсцене**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="8d661-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="8d661-509">Регистрация события щелчка левой кнопкой мыши, чтобы позволить пользователю перетаскивать объекты вокруг сцены.</span><span class="sxs-lookup"><span data-stu-id="8d661-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="8d661-510">Сериализация данных объекта из этой сцены Unity и отправка их в приложение-функция Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="8d661-511">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="8d661-511">To create this class:</span></span>

1.  <span data-ttu-id="8d661-512">Щелкните правой кнопкой мыши папку **Asset** , расположенную на панели проект, и выберите **создать** > **папку**.</span><span class="sxs-lookup"><span data-stu-id="8d661-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="8d661-513">Назовите папку **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="8d661-513">Name the folder **Scripts**.</span></span>

    ![создать папку скриптов](images/AzureLabs-Lab8-66.png)

    ![Папка создания скриптов 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="8d661-516">Дважды щелкните только что созданную папку, чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="8d661-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="8d661-517">Щелкните правой кнопкой мыши внутри папки Scripts и выберите команду **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="8d661-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="8d661-518">Назовите сценарий **таблетосцене**.</span><span class="sxs-lookup"><span data-stu-id="8d661-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="8d661-519">![новый скрипт](images/AzureLabs-Lab8-68.png)
    ![c# таблетосцене переименование](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="8d661-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="8d661-520">Дважды щелкните скрипт, чтобы открыть его в Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8d661-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="8d661-521">Добавьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="8d661-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="8d661-522">В классе вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="8d661-522">Within the class, insert the following variables:</span></span>

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
    > <span data-ttu-id="8d661-523">Замените значение **AccountName** на имя службы хранилища Azure и значение **accountKey** значением ключа, которое находится в службе хранилища Azure, на портале Azure (см. изображение ниже).</span><span class="sxs-lookup"><span data-stu-id="8d661-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![получение ключа учетной записи](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="8d661-525">Теперь добавьте методы **Start ()** и **спящего режима ()** для инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="8d661-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

8.  <span data-ttu-id="8d661-526">В классе **таблетосцене** добавьте метод, который будет получать значения из таблицы Azure и использовать их для порождения соответствующих примитивов в сцене.</span><span class="sxs-lookup"><span data-stu-id="8d661-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

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

9.  <span data-ttu-id="8d661-527">За пределами класса **таблетосцене** необходимо определить класс, используемый приложением для сериализации и десериализации **сущностей таблицы**.</span><span class="sxs-lookup"><span data-stu-id="8d661-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

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

10. <span data-ttu-id="8d661-528">**Сохраните** данные перед возвратом в редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="8d661-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="8d661-529">Щелкните **главную камеру** на панели **Иерархия** , чтобы ее свойства отображались в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="8d661-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="8d661-530">Откройте папку **скрипты** , выберите **файл скрипт таблетосцене** и перетащите его на **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="8d661-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="8d661-531">Результат должен быть следующим:</span><span class="sxs-lookup"><span data-stu-id="8d661-531">The result should be as below:</span></span>

    ![Добавить скрипт в основную камеру](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="8d661-533">Глава 10. Создание класса Клаудсцене в проекте Unity для настольных систем</span><span class="sxs-lookup"><span data-stu-id="8d661-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="8d661-534">Второй сценарий, который необходимо создать, — это **клаудсцене**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="8d661-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="8d661-535">Регистрация события щелчка левой кнопкой мыши, чтобы позволить пользователю перетаскивать объекты вокруг сцены.</span><span class="sxs-lookup"><span data-stu-id="8d661-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="8d661-536">Сериализация данных объекта из этой сцены Unity и отправка их в приложение-функция Azure.</span><span class="sxs-lookup"><span data-stu-id="8d661-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="8d661-537">Чтобы создать второй скрипт, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-537">To create the second script:</span></span>

1.  <span data-ttu-id="8d661-538">Щелкните правой кнопкой мыши в папке Scripts и выберите **создать**, а затем — **Сценарий C\#** .</span><span class="sxs-lookup"><span data-stu-id="8d661-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="8d661-539">Назовите сценарий **клаудсцене**</span><span class="sxs-lookup"><span data-stu-id="8d661-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="8d661-540">![новый скрипт](images/AzureLabs-Lab8-72.png)
    ![c# переименование клаудсцене](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="8d661-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="8d661-541">Добавьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="8d661-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="8d661-542">Вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="8d661-542">Insert the following variables:</span></span>

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

4.  <span data-ttu-id="8d661-543">Замените значение **азурефунктионендпоинт** URL-адресом приложение-функция Azure, который находится в службе приложение-функция Azure, на портале Azure, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="8d661-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![Получить URL-адрес функции](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="8d661-545">Теперь добавьте методы **Start ()** и **спящего режима ()** для инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="8d661-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

6.  <span data-ttu-id="8d661-546">В методе **Update ()** добавьте следующий код, который определит ввод и перетаскивание мыши, который, в свою очередь, переместит объекты gameobject в сцене.</span><span class="sxs-lookup"><span data-stu-id="8d661-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="8d661-547">Если пользователь переместил и удалил объект, он передаст имя и координаты объекта методу **упдатеклаудсцене ()** , который вызывает службу Azure приложение-функция, которая будет обновлять таблицу Azure и активировать уведомление.</span><span class="sxs-lookup"><span data-stu-id="8d661-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

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

7.  <span data-ttu-id="8d661-548">Теперь добавьте метод **упдатеклаудсцене ()** , как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="8d661-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

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

8.  <span data-ttu-id="8d661-549">Сохранение кода и возврат в Unity</span><span class="sxs-lookup"><span data-stu-id="8d661-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="8d661-550">Перетащите сценарий **клаудсцене** на **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="8d661-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="8d661-551">Щелкните **главную камеру** на панели **Иерархия** , чтобы ее свойства отображались в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="8d661-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="8d661-552">После открытия папки Scripts (скрипты) выберите сценарий **клаудсцене** и перетащите его на **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="8d661-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="8d661-553">Результат должен быть следующим:</span><span class="sxs-lookup"><span data-stu-id="8d661-553">The result should be as below:</span></span>

        > ![Перетащите облачный скрипт на основную камеру](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="8d661-555">Глава 11. Создание проекта для настольных систем в UWP</span><span class="sxs-lookup"><span data-stu-id="8d661-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="8d661-556">Все, что необходимо для раздела Unity этого проекта, теперь завершено.</span><span class="sxs-lookup"><span data-stu-id="8d661-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="8d661-557">Перейдите к **параметрам сборки** (**параметры сборки** **файлов** > ).</span><span class="sxs-lookup"><span data-stu-id="8d661-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="8d661-558">В окне " **параметры сборки** " щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="8d661-558">From the **Build Settings** window, click **Build**.</span></span>

    ![проект сборки](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="8d661-560">Откроется окно **проводника** , в котором будет предложено создать расположение для сборки.</span><span class="sxs-lookup"><span data-stu-id="8d661-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="8d661-561">Создайте новую папку (щелкнув **создать папку** в левом верхнем углу) и назовите ее **Build**.</span><span class="sxs-lookup"><span data-stu-id="8d661-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![создать папку для сборки](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="8d661-563">Откройте папку "новые **сборки** " и создайте другую папку (с помощью **новой папки** еще раз) и назовите **ее\_NH\_Desktop App**.</span><span class="sxs-lookup"><span data-stu-id="8d661-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![имя папки NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="8d661-565">Выбрав **\_классическое\_приложение NH** .</span><span class="sxs-lookup"><span data-stu-id="8d661-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="8d661-566">Щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="8d661-566">click **Select Folder**.</span></span> <span data-ttu-id="8d661-567">Построение проекта займет около минуты.</span><span class="sxs-lookup"><span data-stu-id="8d661-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="8d661-568">После сборки появится **окно проводника** , в котором отображается расположение нового проекта.</span><span class="sxs-lookup"><span data-stu-id="8d661-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="8d661-569">Однако не нужно открывать его, так как сначала необходимо создать другой проект Unity в следующих нескольких главах.</span><span class="sxs-lookup"><span data-stu-id="8d661-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="8d661-570">Глава 12. Настройка проекта Unity смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="8d661-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="8d661-571">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="8d661-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="8d661-572">Откройте **Unity** и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="8d661-572">Open **Unity** and click **New**.</span></span>

    ![новый проект Unity](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="8d661-574">Теперь необходимо указать имя проекта Unity, вставить **унитимрнотифхуб**.</span><span class="sxs-lookup"><span data-stu-id="8d661-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="8d661-575">Убедитесь, что для типа проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="8d661-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="8d661-576">Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="8d661-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="8d661-577">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="8d661-577">Then, click **Create project**.</span></span>

    ![имя Унитимрнотифхуб](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="8d661-579">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8d661-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="8d661-580">Перейдите к разделу **изменение** > **настроек** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="8d661-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="8d661-581">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="8d661-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="8d661-582">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="8d661-582">Close the **Preferences** window.</span></span>

    ![присвоить внешнему редактору VS](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="8d661-584">Затем перейдите в раздел**параметры сборки** **файлов** > и переключите платформу на **универсальная платформа Windows**, нажав кнопку коммутатора на **платформе** .</span><span class="sxs-lookup"><span data-stu-id="8d661-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Переключение платформ в UWP](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="8d661-586">Перейдите в раздел**параметры сборки** **файлов** > и убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="8d661-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="8d661-587">**Целевое устройство** настроено для **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="8d661-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="8d661-588">Для Microsoft HoloLens задайте для параметра **целевое устройство** значение *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="8d661-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="8d661-589">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="8d661-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="8d661-590">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="8d661-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="8d661-591">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="8d661-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="8d661-592">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="8d661-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="8d661-593">Здесь стоит сохранить сцену и добавить ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="8d661-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="8d661-594">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="8d661-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="8d661-595">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="8d661-595">A save window will appear.</span></span>

            ![Добавление открытых сцен](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="8d661-597">Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="8d661-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Новая папка сцен](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="8d661-599">Откройте только что созданную папку **сцены** , а затем в поле **имя файла:** введите **\_NH MR\_сцены**и нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="8d661-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![Новая сцена — NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="8d661-601">Оставшиеся параметры, в **параметрах сборки**, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8d661-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="8d661-602">В том же окне нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится **инспектор** .</span><span class="sxs-lookup"><span data-stu-id="8d661-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![открыть параметры проигрывателя](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="8d661-604">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="8d661-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="8d661-605">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="8d661-606">Должна быть **экспериментальная** **версия среды выполнения сценариев** (эквивалент .NET 4,6)</span><span class="sxs-lookup"><span data-stu-id="8d661-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="8d661-607">**Серверная часть сценариев** должна быть ***.NET***</span><span class="sxs-lookup"><span data-stu-id="8d661-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="8d661-608">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="8d661-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![совместимость API](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="8d661-610">На панели в **параметрах XR** (см. ниже **Параметры публикации**), поддерживаемая **Виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="8d661-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![обновить параметры XR](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="8d661-612">На вкладке **Параметры публикации** в разделе **возможности**:</span><span class="sxs-lookup"><span data-stu-id="8d661-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="8d661-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="8d661-613">**InternetClient**</span></span>           

            ![Клиент Tick Internet](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="8d661-615">Вернувшись в **параметры сборки**, **проекты C# Unity** больше не заключаются: установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="8d661-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="8d661-616">После внесения этих изменений закройте окно параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="8d661-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="8d661-617">Сохраните сцену и **файл** > проекта**сохранить сцену/файл** > **сохранить проект**.</span><span class="sxs-lookup"><span data-stu-id="8d661-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8d661-618">Если вы хотите пропустить компонент *настройки Unity* для этого проекта (приложение Mixed Reality) и продолжить работу с кодом, [Скачайте этот файл. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), импортируйте его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте [ Глава 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="8d661-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="8d661-619">Все равно потребуется добавить компоненты скрипта.</span><span class="sxs-lookup"><span data-stu-id="8d661-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="8d661-620">Глава 13. импорт библиотек DLL в проекте Unity смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="8d661-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="8d661-621">Вы будете использовать службу хранилища Azure для библиотеки Unity (которая использует пакет SDK для .NET для Azure).</span><span class="sxs-lookup"><span data-stu-id="8d661-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="8d661-622">Перейдите по этой [ссылке, чтобы использовать службу хранилища Azure с Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="8d661-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="8d661-623">В Unity существует известная ошибка, которая требует перенастройки подключаемых модулей после импорта.</span><span class="sxs-lookup"><span data-stu-id="8d661-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="8d661-624">Эти действия (4-7 в этом разделе) больше не понадобятся после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="8d661-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="8d661-625">Чтобы импортировать пакет SDK в собственный проект, убедитесь, что вы скачали последнюю версию [. пакет unitypackage](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="8d661-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="8d661-626">Затем выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-626">Then, do the following:</span></span>

1.  <span data-ttu-id="8d661-627">Добавьте файл. пакет unitypackage, скачанный из приведенных выше, в Unity с помощью команды меню**настраиваемый пакет** для**импорта** >  **активов** > .</span><span class="sxs-lookup"><span data-stu-id="8d661-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="8d661-628">В появившемся окне **Импорт пакета Unity** можно выбрать все в разделе**хранилище**подключаемых **модулей** > .</span><span class="sxs-lookup"><span data-stu-id="8d661-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![Импорт пакета](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="8d661-630">Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="8d661-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="8d661-631">Перейдите в папку **хранилища** подключаемых **модулей** в представлении проекта и выберите *только*следующие подключаемые модули:</span><span class="sxs-lookup"><span data-stu-id="8d661-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="8d661-632">Microsoft. Data. EDM</span><span class="sxs-lookup"><span data-stu-id="8d661-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="8d661-633">Microsoft. Data. OData</span><span class="sxs-lookup"><span data-stu-id="8d661-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="8d661-634">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="8d661-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="8d661-635">Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="8d661-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="8d661-636">System. пространственные</span><span class="sxs-lookup"><span data-stu-id="8d661-636">System.Spatial</span></span>

    ![Выбор подключаемых модулей](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="8d661-638">Выбрав *нужные подключаемые модули* , **снимите флажок для** **любой платформы** и **снимите флажок** **всаплайер** , а затем нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="8d661-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![применить изменения платформы](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="8d661-640">Эти отдельные подключаемые модули помечаются для использования только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="8d661-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="8d661-641">Это связано с тем, что в папке WSA существуют разные версии тех же подключаемых модулей, которые будут использоваться после экспорта проекта из Unity.</span><span class="sxs-lookup"><span data-stu-id="8d661-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="8d661-642">В папке подключаемый модуль **хранилища** выберите только:</span><span class="sxs-lookup"><span data-stu-id="8d661-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="8d661-643">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="8d661-643">Microsoft.Data.Services.Client</span></span>

        ![Выбор клиента служб данных](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="8d661-645">Установите флажок **не обрабатывать** в разделе **параметры платформы** и нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="8d661-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![не обрабатывать](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="8d661-647">Вы помечаете этот подключаемый модуль как "не обрабатывать", так как у него возникли трудности с обработкой этого подключаемого модуля.</span><span class="sxs-lookup"><span data-stu-id="8d661-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="8d661-648">Подключаемый модуль по-прежнему будет работать, даже если он не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="8d661-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="8d661-649">Глава 14. Создание класса Таблетосцене в проекте Unity для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="8d661-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="8d661-650">Класс **таблетосцене** идентичен описанному в [главе 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="8d661-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="8d661-651">Создайте тот же класс в проекте Unity смешанной реальности, следуя той же процедуре, описанной в [главе 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="8d661-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="8d661-652">После завершения этой главы в обоих **проектах Unity** этот класс будет настроен на основной камере.</span><span class="sxs-lookup"><span data-stu-id="8d661-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="8d661-653">Глава 15. Создание класса Нотификатионрецеивер в проекте Unity для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="8d661-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="8d661-654">Второй сценарий, который необходимо создать, — это **нотификатионрецеивер**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="8d661-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="8d661-655">Регистрация приложения в центре уведомлений при инициализации.</span><span class="sxs-lookup"><span data-stu-id="8d661-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="8d661-656">Прослушивание уведомлений, поступающих от концентратора уведомлений.</span><span class="sxs-lookup"><span data-stu-id="8d661-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="8d661-657">Десериализация данных объекта из полученных уведомлений.</span><span class="sxs-lookup"><span data-stu-id="8d661-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="8d661-658">Переместить объекты gameobject в сцене на основе десериализованных данных.</span><span class="sxs-lookup"><span data-stu-id="8d661-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="8d661-659">Чтобы создать скрипт **нотификатионрецеивер** , выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="8d661-660">Щелкните правой кнопкой мыши в папке Scripts и выберите **создать**, а затем — **Сценарий C\#** .</span><span class="sxs-lookup"><span data-stu-id="8d661-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="8d661-661">Назовите сценарий **нотификатионрецеивер**.</span><span class="sxs-lookup"><span data-stu-id="8d661-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="8d661-662">![Создание нового имени сценария](images/AzureLabs-Lab8-95.png)
    ![c#, нотификатионрецеивер](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="8d661-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="8d661-663">Дважды щелкните скрипт, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="8d661-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="8d661-664">Добавьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="8d661-664">Add the following namespaces:</span></span>

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

4.  <span data-ttu-id="8d661-665">Вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="8d661-665">Insert the following variables:</span></span>

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

5.  <span data-ttu-id="8d661-666">Замените значение **hubName** на имя службы центра уведомлений и значение **хублистенендпоинт** на значение конечной точки на вкладке политики доступа (служба концентратора уведомлений Azure) на портале Azure (см. изображение ниже).</span><span class="sxs-lookup"><span data-stu-id="8d661-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![вставить конечную точку политики концентраторов уведомлений](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="8d661-668">Теперь добавьте методы **Start ()** и **спящего режима ()** для инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="8d661-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

7.  <span data-ttu-id="8d661-669">Добавьте метод **ваитфорнотификатион** , чтобы разрешить приложению получать уведомления из библиотеки концентратора уведомлений без конфликта с основным потоком:</span><span class="sxs-lookup"><span data-stu-id="8d661-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

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

8.  <span data-ttu-id="8d661-670">Следующий метод, **инитнотификатионасинк ()** , будет регистрировать приложение в службе концентратора уведомлений при инициализации.</span><span class="sxs-lookup"><span data-stu-id="8d661-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="8d661-671">Код записывается в комментарий, так как Unity не сможет построить проект.</span><span class="sxs-lookup"><span data-stu-id="8d661-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="8d661-672">Комментарии будут удалены при импорте пакета NuGet для обмена сообщениями Azure в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d661-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

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

9.  <span data-ttu-id="8d661-673">Следующий обработчик **Channel\_пушнотификатионрецеивед ()** будет срабатывать при каждом получении уведомления.</span><span class="sxs-lookup"><span data-stu-id="8d661-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="8d661-674">Будет выполнена десериализация уведомления, которое будет являться сущностью таблицы Azure, перемещенной в классическое приложение, а затем переместить соответствующий GameObject в сцене с той же позицией.</span><span class="sxs-lookup"><span data-stu-id="8d661-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="8d661-675">Код записывается в комментарий, поскольку код ссылается на библиотеку обмена сообщениями Azure, которую вы добавите после сборки проекта Unity с помощью диспетчера пакетов NuGet в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d661-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="8d661-676">Таким образом, проект Unity не сможет выполнить сборку, пока не будет добавлен в комментарий. Имейте в виду, что при построении проекта и последующем возврате к Unity необходимо будет **повторно закомментировать** этот код.</span><span class="sxs-lookup"><span data-stu-id="8d661-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

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

10. <span data-ttu-id="8d661-677">Не забудьте сохранить изменения перед возвратом в редактор Unity.</span><span class="sxs-lookup"><span data-stu-id="8d661-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="8d661-678">Щелкните **главную камеру** на панели **Иерархия** , чтобы ее свойства отображались в инспекторе.</span><span class="sxs-lookup"><span data-stu-id="8d661-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="8d661-679">После открытия папки Scripts (скрипты) выберите сценарий **нотификатионрецеивер** и перетащите его на **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="8d661-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="8d661-680">Результат должен быть следующим:</span><span class="sxs-lookup"><span data-stu-id="8d661-680">The result should be as below:</span></span>

    ![Перетащите скрипт получателя уведомлений на камеру](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="8d661-682">Если вы разрабатываете это для Microsoft HoloLens, необходимо обновить компонент *камеры* **основной камеры**, чтобы:</span><span class="sxs-lookup"><span data-stu-id="8d661-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="8d661-683">Снять флаги: Сплошной цвет</span><span class="sxs-lookup"><span data-stu-id="8d661-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="8d661-684">Днем Черный</span><span class="sxs-lookup"><span data-stu-id="8d661-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="8d661-685">Глава 16. Создание проекта смешанной реальности для UWP</span><span class="sxs-lookup"><span data-stu-id="8d661-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="8d661-686">Эта глава идентична процессу сборки для предыдущего проекта.</span><span class="sxs-lookup"><span data-stu-id="8d661-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="8d661-687">Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.</span><span class="sxs-lookup"><span data-stu-id="8d661-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="8d661-688">Перейдите к **параметрам сборки** (**параметры сборки** **файлов** > ).</span><span class="sxs-lookup"><span data-stu-id="8d661-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="8d661-689">В меню **параметры сборки** убедитесь, что **проект C# Unity**\* является тактовым (что позволит изменять скрипты в этом проекте после сборки).</span><span class="sxs-lookup"><span data-stu-id="8d661-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="8d661-690">По завершении нажмите кнопку **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="8d661-690">After this is done, click **Build**.</span></span>

    ![проект сборки](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="8d661-692">Откроется окно **проводника** , в котором будет предложено создать расположение для сборки.</span><span class="sxs-lookup"><span data-stu-id="8d661-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="8d661-693">Создайте новую папку (щелкнув **создать папку** в левом верхнем углу) и назовите ее **Build**.</span><span class="sxs-lookup"><span data-stu-id="8d661-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![создать папку сборок](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="8d661-695">Откройте папку "новые **сборки** " и создайте другую папку (с помощью **новой папки** еще раз) и назовите ее **\_NH\_-приложение MR**.</span><span class="sxs-lookup"><span data-stu-id="8d661-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![создать папку NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="8d661-697">Выбрав **приложение NH\_MR\_** .</span><span class="sxs-lookup"><span data-stu-id="8d661-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="8d661-698">Щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="8d661-698">click **Select Folder**.</span></span> <span data-ttu-id="8d661-699">Построение проекта займет около минуты.</span><span class="sxs-lookup"><span data-stu-id="8d661-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="8d661-700">После сборки откроется окно **проводника** , в котором находится новый проект.</span><span class="sxs-lookup"><span data-stu-id="8d661-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="8d661-701">Глава 17. Добавление пакетов NuGet в решение Унитимрнотифхуб</span><span class="sxs-lookup"><span data-stu-id="8d661-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="8d661-702">Помните, что после добавления следующих пакетов NuGet (и раскомментируйте код в следующей [главе](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)) код, при повторном открытии в проекте Unity, будет представлять ошибки.</span><span class="sxs-lookup"><span data-stu-id="8d661-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="8d661-703">Если вы хотите вернуться и продолжить редактирование в редакторе Unity, вам потребуется комментарий, ерросоме код, а затем раскомментировать его позже, как только вы вернетесь в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d661-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="8d661-704">После завершения сборки Mixed Reality перейдите к проекту Mixed Reality, который вы создали, и дважды щелкните файл решения (SLN) в этой папке, чтобы открыть решение с помощью Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8d661-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="8d661-705">Теперь необходимо добавить пакет NuGet **WindowsAzure. Messaging. Managed.** это библиотека, которая используется для получения уведомлений из центра уведомлений.</span><span class="sxs-lookup"><span data-stu-id="8d661-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="8d661-706">Чтобы импортировать пакет NuGet, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="8d661-707">В **Обозреватель решений**щелкните решение правой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="8d661-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="8d661-708">Щелкните **Управление пакетами NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8d661-708">Click on **Manage NuGet Packages**.</span></span>

    ![открыть диспетчер NuGet](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="8d661-710">Выберите вкладку ***Обзор*** и выполните поиск по запросу **WindowsAzure. Messaging. Managed**.</span><span class="sxs-lookup"><span data-stu-id="8d661-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![Поиск пакета Windows Azure Messaging](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="8d661-712">Выберите результат (как показано ниже) и в окне справа установите флажок рядом с пунктом **проект**.</span><span class="sxs-lookup"><span data-stu-id="8d661-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="8d661-713">Он поместит такт в флажок рядом с **Project**, а также флажок рядом с проектом **Сборка — CSharp** и **унитимрнотифхуб** .</span><span class="sxs-lookup"><span data-stu-id="8d661-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![тикать все проекты](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="8d661-715">Изначально указанная версия **может** быть несовместима с этим проектом.</span><span class="sxs-lookup"><span data-stu-id="8d661-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="8d661-716">Поэтому щелкните раскрывающееся меню рядом с пунктом **Version (версия**) и выберите **Version 0.1.7.9 (версия**), а затем нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="8d661-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="8d661-717">Установка пакета NuGet завершена.</span><span class="sxs-lookup"><span data-stu-id="8d661-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="8d661-718">Найдите код с комментарием, введенный в классе **нотификатионрецеивер** , и удалите комментарии.</span><span class="sxs-lookup"><span data-stu-id="8d661-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="8d661-719">Глава 18 — изменение приложения Унитимрнотифхуб, класс Нотификатионрецеивер</span><span class="sxs-lookup"><span data-stu-id="8d661-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="8d661-720">После добавления **пакетов NuGet**необходимо раскомментировать часть кода в классе **нотификатионрецеивер** .</span><span class="sxs-lookup"><span data-stu-id="8d661-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="8d661-721">Сюда входят следующие возможности.</span><span class="sxs-lookup"><span data-stu-id="8d661-721">This includes:</span></span>

1. <span data-ttu-id="8d661-722">Пространство имен в верхней части:</span><span class="sxs-lookup"><span data-stu-id="8d661-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="8d661-723">Весь код в методе **InitNotificationsAsync ()** :</span><span class="sxs-lookup"><span data-stu-id="8d661-723">All the code within the **InitNotificationsAsync()** method:</span></span>

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
> <span data-ttu-id="8d661-724">В приведенном выше коде есть комментарий: Убедитесь, что вы случайно не изменили *комментирование* комментария (так как код не будет компилироваться, если у вас есть!).</span><span class="sxs-lookup"><span data-stu-id="8d661-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="8d661-725">И наконец, событие **Channel_PushNotificationReceived** :</span><span class="sxs-lookup"><span data-stu-id="8d661-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

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

<span data-ttu-id="8d661-726">Выполнив эти комментарии, убедитесь, что вы сохранили, а затем переходите к следующей главе.</span><span class="sxs-lookup"><span data-stu-id="8d661-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="8d661-727">Глава 19. Связывание проекта Mixed Reality с приложением магазина</span><span class="sxs-lookup"><span data-stu-id="8d661-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="8d661-728">Теперь необходимо связать проект **Mixed Reality** с приложением магазина, созданным в начале лаборатории.</span><span class="sxs-lookup"><span data-stu-id="8d661-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="8d661-729">Откройте решение.</span><span class="sxs-lookup"><span data-stu-id="8d661-729">Open the solution.</span></span>

2.  <span data-ttu-id="8d661-730">Щелкните правой кнопкой мыши проект приложения UWP на панели обозреватель решений, выберите **магазин**и **свяжите приложение с магазином...**</span><span class="sxs-lookup"><span data-stu-id="8d661-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![открыть ассоциацию магазина](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="8d661-732">Появится новое окно **с именем связать приложение с магазином Windows**.</span><span class="sxs-lookup"><span data-stu-id="8d661-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="8d661-733">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="8d661-733">Click **Next**.</span></span>

    ![Переход к следующему экрану](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="8d661-735">Будут загружены все приложения, связанные с учетной записью, с которой вы выполнили вход.</span><span class="sxs-lookup"><span data-stu-id="8d661-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="8d661-736">Если вы не вошли в учетную запись, вы можете **войти** на эту страницу.</span><span class="sxs-lookup"><span data-stu-id="8d661-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="8d661-737">Найдите **имя приложения Магазина** , созданное в начале этого руководства, и выберите его.</span><span class="sxs-lookup"><span data-stu-id="8d661-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="8d661-738">Затем нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="8d661-738">Then click **Next**.</span></span>

    ![Найдите и выберите имя вашего магазина.](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="8d661-740">Нажмите кнопку **связать**.</span><span class="sxs-lookup"><span data-stu-id="8d661-740">Click **Associate**.</span></span>

    ![связать приложение](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="8d661-742">Теперь ваше приложение **связано** с приложением магазина.</span><span class="sxs-lookup"><span data-stu-id="8d661-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="8d661-743">Это необходимо для включения уведомлений.</span><span class="sxs-lookup"><span data-stu-id="8d661-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="8d661-744">Глава 20. Развертывание приложений Унитимрнотифхуб и Унитидесктопнотифхуб</span><span class="sxs-lookup"><span data-stu-id="8d661-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="8d661-745">Эта глава может быть проще с двумя людьми, так как в результате будут включены оба приложения, работающие на рабочем столе компьютера, а другая — в иммерсивное гарнитуру.</span><span class="sxs-lookup"><span data-stu-id="8d661-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="8d661-746">Иммерсивное приложение в гарнитуре ожидает получения изменений в сцене (изменение расположения локальных объекты gameobject), а классическое приложение будет вносить изменения в локальную сцену (изменения позиционирования), которые будут использоваться совместно с приложением MR.</span><span class="sxs-lookup"><span data-stu-id="8d661-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="8d661-747">Имеет смысл сначала развернуть приложение MR, а затем классическое приложение, чтобы получатель мог начать прослушивание.</span><span class="sxs-lookup"><span data-stu-id="8d661-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="8d661-748">Чтобы развернуть приложение **унитимрнотифхуб** на локальном компьютере, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="8d661-749">Откройте файл решения приложения **унитимрнотифхуб** в **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="8d661-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="8d661-750">На **платформе решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="8d661-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="8d661-751">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="8d661-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![Задание конфигурации проекта](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="8d661-753">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8d661-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="8d661-754">Теперь приложение должно отобразиться в списке установленных приложений, готовых к запуску.</span><span class="sxs-lookup"><span data-stu-id="8d661-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="8d661-755">Чтобы развернуть приложение **унитидесктопнотифхуб** на локальном компьютере, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="8d661-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="8d661-756">Откройте файл решения приложения **унитидесктопнотифхуб** в **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="8d661-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="8d661-757">На **платформе решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="8d661-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="8d661-758">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="8d661-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![Задание конфигурации проекта](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="8d661-760">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение на компьютере.</span><span class="sxs-lookup"><span data-stu-id="8d661-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="8d661-761">Теперь приложение должно отобразиться в списке установленных приложений, готовых к запуску.</span><span class="sxs-lookup"><span data-stu-id="8d661-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="8d661-762">Запустите приложение Mixed Reality, а затем настольное приложение.</span><span class="sxs-lookup"><span data-stu-id="8d661-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="8d661-763">При запуске обоих приложений переместите объект в классической сцене (с помощью левой кнопки мыши).</span><span class="sxs-lookup"><span data-stu-id="8d661-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="8d661-764">Эти позиционированные изменения будут сделаны локально, сериализованы и отправлены в службу приложение-функция.</span><span class="sxs-lookup"><span data-stu-id="8d661-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="8d661-765">Затем служба приложение-функция обновит таблицу вместе с концентратором уведомлений.</span><span class="sxs-lookup"><span data-stu-id="8d661-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="8d661-766">После получения обновления Центр уведомлений отправит обновленные данные непосредственно во все зарегистрированные приложения (в данном случае это приложение для иммерсивного гарнитуры), которое затем десериализует входящие данные и применяет новые позиционированные данные к локальным объектам. их перемещение в сцене.</span><span class="sxs-lookup"><span data-stu-id="8d661-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="8d661-767">Ваше приложение для центров уведомлений Azure завершено</span><span class="sxs-lookup"><span data-stu-id="8d661-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="8d661-768">Поздравляем, вы создали приложение смешанной реальности, которое использует службу концентраторов уведомлений Azure и разрешают обмен данными между приложениями.</span><span class="sxs-lookup"><span data-stu-id="8d661-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![окончательный конец продукта](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="8d661-770">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="8d661-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="8d661-771">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="8d661-771">Exercise 1</span></span>

<span data-ttu-id="8d661-772">Можно ли изменить цвет объекты gameobject и отправить это уведомление другим приложениям, просматривающим сцену?</span><span class="sxs-lookup"><span data-stu-id="8d661-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="8d661-773">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="8d661-773">Exercise 2</span></span>

<span data-ttu-id="8d661-774">Можно ли добавить перемещение объекты gameobject в приложение MR и просмотреть обновленную сцену в классическом приложении?</span><span class="sxs-lookup"><span data-stu-id="8d661-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
