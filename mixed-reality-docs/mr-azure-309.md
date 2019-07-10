---
title: Г-н и 309 Azure - Application insights
description: Выполните этот курс, чтобы узнать, как для сбора аналитики в отношении поведения пользователей приложения смешанной реальности, с помощью службы Azure Application Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, application insights, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694563"
---
>[!NOTE]
><span data-ttu-id="8c2d7-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8c2d7-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8c2d7-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8c2d7-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8c2d7-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8c2d7-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="8c2d7-110">Г-н и Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="8c2d7-110">MR and Azure 309: Application insights</span></span>

![конечный продукт-запуск](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="8c2d7-112">В рамках этого курса вы узнаете, как для добавления возможностей Application Insights с приложением смешанной реальности, с помощью Azure Application Insights API для сбора аналитики о поведении пользователей.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="8c2d7-113">Application Insights — службе Майкрософт, позволяя разработчикам сбора аналитики из своих приложений и управлять им с помощью портала к использованию.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="8c2d7-114">Аналитики может быть что угодно — от производительности для пользовательских сведений, которые вы хотите собирать.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="8c2d7-115">Дополнительные сведения см. в статье [страница Application Insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="8c2d7-116">После выполнения этого курса, у вас будет приложение иммерсивных гарнитуры смешанной реальности, которое сможет выполнить следующие:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="8c2d7-117">Разрешает пользователю помощи и перемещать сцены.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="8c2d7-118">Инициировать отправку analytics для *служба Application Insights*, за счет использования взглядом и близости от объектов сцены.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="8c2d7-119">Приложение также будет вызывать службу, получение сведений о том, что о какой объект был к наиболее пользователем, за последние 24 часа.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="8c2d7-120">Этот объект будет изменить его цвет зеленый цвет.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-120">That object will change its color to green.</span></span>

<span data-ttu-id="8c2d7-121">Этот курс ознакомят вас для получения результатов из службы Application Insights в приложение на базе Unity образец.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="8c2d7-122">Это будет необходимо применение этих понятий в пользовательское приложение, возможно, вы разрабатываете.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="8c2d7-123">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="8c2d7-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8c2d7-124">Курс</span><span class="sxs-lookup"><span data-stu-id="8c2d7-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8c2d7-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c2d7-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c2d7-126"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="8c2d7-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="8c2d7-127">Г-н и Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="8c2d7-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c2d7-128">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2d7-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c2d7-129">✔️</span><span class="sxs-lookup"><span data-stu-id="8c2d7-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="8c2d7-130">Хотя этот курс основное внимание уделяется Windows Mixed Reality иммерсивную (VR), можно также применить полученные знания в этом курсе для Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="8c2d7-131">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="8c2d7-132">При использовании HoloLens, вы можете заметить некоторые echo во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c2d7-133">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="8c2d7-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="8c2d7-134">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="8c2d7-135">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="8c2d7-136">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="8c2d7-137">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="8c2d7-138">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="8c2d7-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="8c2d7-139">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="8c2d7-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8c2d7-140">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="8c2d7-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8c2d7-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="8c2d7-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8c2d7-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8c2d7-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="8c2d7-143">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="8c2d7-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="8c2d7-144">Наушники с помощью встроенного микрофона (если гарнитура не имеет встроенных mic, а также докладчиков)</span><span class="sxs-lookup"><span data-stu-id="8c2d7-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="8c2d7-145">Доступ к Интернету для настройки Azure и получения данных Application Insights</span><span class="sxs-lookup"><span data-stu-id="8c2d7-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="8c2d7-146">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="8c2d7-146">Before you start</span></span>

<span data-ttu-id="8c2d7-147">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="8c2d7-148">Имейте в виду, данные, передаваемые *Application Insights* занимает некоторое время, поэтому будьте пациента.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="8c2d7-149">Если вы хотите проверить, если служба получила данные, см. статью [Глава 14](#chapter-14---the-application-insights-service-portal), где будет показано как перейти на портал.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="8c2d7-150">Глава 1 - портала Azure</span><span class="sxs-lookup"><span data-stu-id="8c2d7-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="8c2d7-151">Чтобы использовать *Application Insights*, вам потребуется создать и настроить *служба Application Insights* на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="8c2d7-152">Войдите в [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="8c2d7-153">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="8c2d7-154">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="8c2d7-155">После входа в систему щелкните **New** в левом верхнем углу, а поиск *Application Insights*и нажмите кнопку **ввод**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8c2d7-156">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="8c2d7-158">Новая страница справа будет предоставить описание *Azure Application Insights* службы.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="8c2d7-159">В нижней левой части этой страницы выберите **создать** кнопку, чтобы создать ассоциацию с данным службы.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="8c2d7-161">Когда вы перейдете на **создать**:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="8c2d7-162">Вставить нужный **имя** для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="8c2d7-163">Как **тип приложения**выберите **Общие**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="8c2d7-164">Выберите соответствующее **подписки**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="8c2d7-165">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="8c2d7-166">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="8c2d7-167">Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="8c2d7-168">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="8c2d7-169">Выберите **расположение**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="8c2d7-170">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="8c2d7-171">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-171">Select **Create**.</span></span>

        ![Портал Azure](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="8c2d7-173">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="8c2d7-174">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="8c2d7-176">Щелкните уведомлений для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="8c2d7-178">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="8c2d7-179">Вы перейдете на новый *служба Application Insights* экземпляра.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="8c2d7-181">Не закрывайте эту веб-страницу и удобный доступ, вам будет вернитесь сюда часто, чтобы просмотреть собранные данные.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8c2d7-182">Чтобы реализовать Application Insights, необходимо будет использовать конкретные значения трех (3): **Ключ инструментирования**, **идентификатор приложения**, и **ключ API**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="8c2d7-183">Ниже показано, как получить эти значения из вашей службы.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="8c2d7-184">Обязательно запишите эти значения на пустое *Блокнот* странице, поскольку будет использовать их только в коде.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="8c2d7-185">Чтобы найти **ключ инструментирования**, вам потребуется прокрутите вниз список функций службы и щелкните **свойства**, показывают отображается вкладка **ключ службы**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="8c2d7-187">Немного ниже **свойства**, вы найдете **доступ через API**, который нужно щелкнуть.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="8c2d7-188">Панель справа предоставит **идентификатор приложения** вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="8c2d7-190">С помощью **идентификатор приложения** панели все еще открыт, выберите **Создание ключа API**, при этом открывается *Создание ключа API* панели.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="8c2d7-192">В рамках открытым теперь *Создание ключа API* панели, введите описание, и **деления три поля**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="8c2d7-193">Нажмите кнопку **создания ключа**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-193">Click **Generate Key**.</span></span> <span data-ttu-id="8c2d7-194">Ваш **ключ API** будет необходимо создать и отобразить.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-194">Your **API Key** will be created and displayed.</span></span> 

    ![Портал Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="8c2d7-196">Это единственный случай, когда ваш **ключ службы** будет отображаться, поэтому убедитесь, вы теперь сделать его копию.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="8c2d7-197">Глава 2 - Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="8c2d7-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="8c2d7-198">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="8c2d7-199">Откройте *Unity* и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-199">Open *Unity* and click **New**.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="8c2d7-201">Введите имя проекта Unity, теперь нужно вставить **MR\_Azure\_приложения\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="8c2d7-202">Убедитесь, что *шаблона* присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="8c2d7-203">Задайте *расположение* в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="8c2d7-204">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-204">Then, click **Create project**.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="8c2d7-206">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="8c2d7-207">Перейдите к **изменить \> предпочтения** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="8c2d7-208">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="8c2d7-209">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-209">Close the **Preferences** window.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="8c2d7-211">Перейдите к **файл \> параметры построения** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **переключения платформы** кнопки.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="8c2d7-213">Перейдите к **файл \> параметры построения** и убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="8c2d7-214">**Целевое устройство** присваивается **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="8c2d7-215">Microsoft HoloLens, задайте **целевое устройство** для *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="8c2d7-216">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="8c2d7-217">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="8c2d7-218">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="8c2d7-219">Сохраните сцены и добавить его к сборке.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="8c2d7-220">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="8c2d7-221">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-221">A save window will appear.</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="8c2d7-223">Создайте новую папку для этого и все будущие сцены, а затем щелкните **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="8c2d7-225">Откройте только что созданный **сцены** папку, а затем в *имя файла:* текстовое поле, тип **ApplicationInsightsScene**, нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="8c2d7-227">Для остальных параметров, в **параметры построения**, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="8c2d7-228">В **параметры построения** щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где **инспектор** находится.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="8c2d7-230">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="8c2d7-231">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="8c2d7-232">**Scripting** **версии среды выполнения** должно быть **экспериментальные (.NET 4.6 эквивалент)** , что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="8c2d7-233">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="8c2d7-234">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="8c2d7-236">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="8c2d7-237">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-237">**InternetClient**</span></span>     

            ![Настройка проекта Unity](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="8c2d7-239">Далее панели в **XR параметры** (под **параметров публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **Windows Mixed Reality Пакет SDK** добавляется.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="8c2d7-241">Вернитесь в **параметры построения**, **Unity C# проекты** больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="8c2d7-242">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="8c2d7-243">Сохраните сцену и проекта (**ФАЙЛ** > **сохранить СЦЕНУ / FILE** > **сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="8c2d7-244">Глава 3 - Импорт пакета Unity</span><span class="sxs-lookup"><span data-stu-id="8c2d7-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c2d7-245">Если вы хотите пропустить *Настройка Unity* компоненты этого курса и по-прежнему непосредственно в код, вы можете загрузить [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="8c2d7-246">Оно также будет содержать библиотеки DLL из следующей главе.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="8c2d7-247">После импорта, по-прежнему из [ **Глава 6**](#chapter-6---create-the-applicationinsightstracker-class).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c2d7-248">Чтобы использовать Application Insights в Unity, необходимо импортировать библиотеку DLL для него, вместе с Newtonsoft DLL.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="8c2d7-249">В Unity, который требует подключаемых модулей, чтобы повторно настроить после импорта в настоящее время имеется известная проблема.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="8c2d7-250">Эти шаги (4 – 7 в этом разделе), не будет обязательным после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="8c2d7-251">Чтобы импортировать Application Insights в свой проект, убедитесь, что у вас есть [загружен «.unitypackage», содержащий подключаемые модули](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="8c2d7-252">Затем сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-252">Then, do the following:</span></span>

1.  <span data-ttu-id="8c2d7-253">Добавить **.unitypackage** к Unity с помощью **активы \> Импорт пакета \> пользовательского пакета** пункт меню.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="8c2d7-254">В **Импорт пакета Unity** который появится убедитесь, что все, что в разделе (вплоть до) **подключаемые модули** выбран.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="8c2d7-256">Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="8c2d7-257">Перейдите к **Insights** папке **подключаемые модули** в проекте можно просматривать и выбирать следующие подключаемые модули *только*:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="8c2d7-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="8c2d7-258">Microsoft.ApplicationInsights</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="8c2d7-260">С этим *подключаемый модуль* выбран, убедитесь, что **Any платформы** — **unchecked**, убедитесь, что флажок **WSAPlayer** также  **unchecked**, затем нажмите кнопку **применить**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="8c2d7-261">Это — просто убедитесь, что файлы настроены правильно.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="8c2d7-263">Пометки подключаемых модулей, например это, настраивает их можно использовать только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="8c2d7-264">Существует другой набор библиотек DLL в папке WSA, которая будет использоваться после проект будет экспортирован из Unity.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="8c2d7-265">Затем необходимо открыть **WSA** папку, в пределах **Insights** папки.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="8c2d7-266">Вы увидите копию тот же файл, который вы только что настроили.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="8c2d7-267">Выберите этот файл и затем в инспекторе, убедитесь, что **Any платформы** — **unchecked**, убедитесь, что флажок **только** **WSAPlayer** является **проверяется**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="8c2d7-268">Щелкните **Применить**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-268">Click **Apply**.</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="8c2d7-270">Теперь необходимо будет выполнить **шаги 4 – 6**, но для *Newtonsoft* подключаемые модули вместо этого.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="8c2d7-271">См. в разделе ниже снимок экрана для результат должен выглядеть так.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="8c2d7-273">Глава 4 – Настройка камеры и пользователем элементы управления</span><span class="sxs-lookup"><span data-stu-id="8c2d7-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="8c2d7-274">В этой главе вы настроите камеры и элементов управления позволяет пользователю см. в разделе и переместите в сцене.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="8c2d7-275">Щелкните правой кнопкой мыши пустую область на панели «иерархии», затем на **создать** > **пустой**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="8c2d7-277">Переименуйте новый пустой объект GameObject для **камеры родительского**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="8c2d7-279">Щелкните правой кнопкой мыши пустую область на панели «иерархии», затем на **трехмерный объект**, то на **Sphere**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="8c2d7-280">Переименовать сферой **правом**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="8c2d7-281">Задайте **преобразование масштабирования** стрелки вправо к **0.1, 0.1, 0,1**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="8c2d7-283">Удалить **Sphere Collider** с правой стороны, щелкнув **шестеренки** в *Sphere Collider* компонента, а затем **удалить компонент** .</span><span class="sxs-lookup"><span data-stu-id="8c2d7-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="8c2d7-285">В панели иерархии перетащите **Main Camera** и **правом** перетаскивание объектов **камеры родительского** объекта.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="8c2d7-287">Задайте **преобразование положения** обоих **Main Camera** и **правом** объект **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-31.png)

    ![Настройка камеры и пользовательские элементы управления](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="8c2d7-290">Глава 5 - Настройка объектов в сцене Unity</span><span class="sxs-lookup"><span data-stu-id="8c2d7-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="8c2d7-291">Теперь вы создадите некоторые основные фигуры для сцены, с помощью которого пользователь может взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="8c2d7-292">Щелкните правой кнопкой мыши пустую область в *панели иерархии*, то на **трехмерный объект**, а затем выберите **плоскости**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="8c2d7-293">Задайте плоскость **преобразование положения** для **0, -1, 0**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="8c2d7-294">Задайте плоскость **преобразование масштабирования** для **5, 1, 5**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="8c2d7-296">Создать базовый материал для использования с вашей **плоскости** объекта, таким образом, проще видеть другие фигуры.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="8c2d7-297">Перейдите к вашей *панель проекта*, щелкните правой кнопкой мыши, затем **создать**, за которым следует **папку**, чтобы создать новую папку.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="8c2d7-298">Назовите его **материалы**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-298">Name it **Materials**.</span></span>

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-34.png) ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="8c2d7-301">Откройте **материалы** папку, а затем щелкните правой кнопкой мыши щелкните **создать**, затем **материал**, чтобы создать новый материал.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="8c2d7-302">Назовите его **синий**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-302">Name it **Blue**.</span></span>

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-36.png) ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="8c2d7-305">С новым **синий** выбран, взгляните на материал *инспектор*и нажмите кнопку прямоугольное окно вместе с **Albedo**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="8c2d7-306">Выберите голубой цвет (один ниже изображен **Hex цвет: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="8c2d7-307">После выбора нажмите кнопку "Закрыть".</span><span class="sxs-lookup"><span data-stu-id="8c2d7-307">Click the close button once you have chosen.</span></span>

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="8c2d7-309">Перетащите новый материал из **материалы** папки, в только что созданный **плоскости**, в сценах (или поместите его на **плоскости** объекта в пределах  *Иерархия*).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="8c2d7-311">Щелкните правой кнопкой мыши пустую область в *панели иерархии*, то на **трехмерного объекта, Capsule**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="8c2d7-312">С помощью **Capsule** , измените его **преобразования** *позиции* для: **-10 "," 1 "," 0**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="8c2d7-313">Щелкните правой кнопкой мыши пустую область в *панели иерархии*, то на **трехмерного объекта, куб**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="8c2d7-314">С помощью **куба** , измените его **преобразования** *позиции* для: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="8c2d7-315">Щелкните правой кнопкой мыши пустую область в *панели иерархии*, то на **трехмерного объекта, Sphere**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="8c2d7-316">С помощью **Sphere** , измените его **преобразования** *позиции* для: **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="8c2d7-318">Эти *позиции* значения: *предложения*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="8c2d7-319">Вы свободны в задается расположение объектов в любое другое, то, что это удобнее для пользователя приложения, если объекты на расстоянии не слишком далеко от камеры.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="8c2d7-320">Когда приложение запущено, необходимо иметь возможность идентифицировать объекты на сцене, чтобы добиться этого, их необходимо отметить тегами.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="8c2d7-321">Выберите один из объектов, а также в *инспектор* панели, щелкните **добавить тег...** , который поменяет *инспектор* с **теги & слои** панели.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="8c2d7-322">![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="8c2d7-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="8c2d7-323">Нажмите кнопку **+ (плюс)** символов, а затем введите имя тега, как **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="8c2d7-325">Если вы используете другое имя для тега, необходимо гарантировать это изменение также *DataFromAnalytics*, *ObjectTrigger*, и *помощи*, более поздней версии, сценарии, чтобы ваши объекты найден и обнаружено, в сценах.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="8c2d7-326">Тег создан необходимо применить его для всех трех объектов.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="8c2d7-327">Из *иерархии*, удерживайте **Shift** ключа, а затем щелкните **Capsule**, **куба**, и **Sphere**, объекты, а затем в *инспектор*, щелкните раскрывающееся меню рядом с **тега**, нажмите кнопку *ObjectInScene* тег был создан.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="8c2d7-328">![Настроить объекты на сцене Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="8c2d7-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="8c2d7-329">Глава 6 - создание класса ApplicationInsightsTracker</span><span class="sxs-lookup"><span data-stu-id="8c2d7-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="8c2d7-330">Первый скрипт, чтобы создать **ApplicationInsightsTracker**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="8c2d7-331">Создание событий, в зависимости от действий пользователя для отправки в Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="8c2d7-332">Создание соответствующие имена событий, в зависимости от взаимодействия с пользователем.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="8c2d7-333">Отправка событий в экземпляре службы Application Insights.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="8c2d7-334">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-334">To create this class:</span></span>

1.  <span data-ttu-id="8c2d7-335">Щелкните правой кнопкой мыши в *проекта панели*, затем **создать** > **папку**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="8c2d7-336">Назовите папку **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-336">Name the folder **Scripts**.</span></span>

    ![Создание класса ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Создание класса ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="8c2d7-339">С помощью **сценариев** папка создана, дважды щелкните его, чтобы открыть.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="8c2d7-340">Затем, внутри этой папки, щелкните правой кнопкой мыши **создать**  >   **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="8c2d7-341">Назовите сценарий **ApplicationInsightsTracker**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="8c2d7-342">Дважды щелкните новый **ApplicationInsightsTracker** скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="8c2d7-343">Обновление пространства имен в верхней части скрипта как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="8c2d7-344">Внутри класса вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="8c2d7-345">Задайте **instrumentationKey, идентификатор приложения и ключа API** значения соответствующим образом, с помощью *ключи службы* на портале Azure, как упоминалось в [главе 1](#chapter-1---the-azure-portal), шаг 9 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="8c2d7-346">Затем добавьте **Start()** и **Awake()** методы, которые будут вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="8c2d7-347">Добавьте методы, отвечающий за отправку событий и метрик, зарегистрированные для приложения.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="8c2d7-348">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="8c2d7-349">Глава 7 - создание скрипта взглядом</span><span class="sxs-lookup"><span data-stu-id="8c2d7-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="8c2d7-350">Далее сценарий для создания **помощи** скрипта.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="8c2d7-351">Этот сценарий отвечает за создание *Raycast* , будет проецироваться вперед от *Main Camera*, для обнаружения какой объект, который просматривает пользователь.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="8c2d7-352">В этом случае *Raycast* будет необходимо определить, если пользователь просматривает объект с **ObjectInScene** тег, а затем подсчитать как долго пользователь *gazes* на этот объект.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="8c2d7-353">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="8c2d7-354">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="8c2d7-355">Назовите сценарий **помощи**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="8c2d7-356">Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="8c2d7-357">Замените существующий код следующим:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="8c2d7-358">Код для **Awake()** и **Start()** методы теперь должен быть добавлен.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="8c2d7-359">Внутри **помощи** добавьте следующий код в **Update()** метод проект *Raycast* и обнаруживать попадание целевой объект:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="8c2d7-360">Добавить **ResetFocusedObject()** метод для отправки данных **Application Insights** когда пользователь открывал объекта.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="8c2d7-361">Вы завершили **помощи** скрипта.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="8c2d7-362">Сохраните изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="8c2d7-363">Глава 8 - создать класс ObjectTrigger</span><span class="sxs-lookup"><span data-stu-id="8c2d7-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="8c2d7-364">Далее необходимо создать сценарий **ObjectTrigger**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="8c2d7-365">Добавление компонентов, необходимых для конфликта в Main Camera.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="8c2d7-366">Обнаружение, если камера находится рядом с объектом, помеченным как **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="8c2d7-367">Для создания скрипта:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-367">To create the script:</span></span>

1.  <span data-ttu-id="8c2d7-368">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="8c2d7-369">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="8c2d7-370">Назовите сценарий **ObjectTrigger**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="8c2d7-371">Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="8c2d7-372">Замените существующий код следующим:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="8c2d7-373">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="8c2d7-374">Глава 9 — создать класс DataFromAnalytics</span><span class="sxs-lookup"><span data-stu-id="8c2d7-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="8c2d7-375">Теперь необходимо будет создать **DataFromAnalytics** сценарий, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="8c2d7-376">Выборка данных аналитики, о том, какие объекта были достиг камеры больше всего.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="8c2d7-377">С помощью *ключи службы*, разрешить связь с экземпляром службы Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="8c2d7-378">Упорядочивание объектов в сцене, в соответствии с которым имеет наибольшее количество событий.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="8c2d7-379">Изменение цветом материала, наиболее approached объекта, к *зеленый*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="8c2d7-380">Для создания скрипта:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-380">To create the script:</span></span>

1.  <span data-ttu-id="8c2d7-381">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="8c2d7-382">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="8c2d7-383">Назовите сценарий **DataFromAnalytics**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="8c2d7-384">Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="8c2d7-385">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="8c2d7-386">Внутри скрипта вставьте следующее:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="8c2d7-387">В рамках **DataFromAnalytics** класса, сразу после **Start()** метод, добавьте следующий метод с именем **FetchAnalytics()** .</span><span class="sxs-lookup"><span data-stu-id="8c2d7-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="8c2d7-388">Этот метод отвечает за заполнение списка пар ключ-значение с *GameObject* и номером число событий заполнителя.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="8c2d7-389">Затем он инициализирует **GetWebRequest()** соподпрограмме.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="8c2d7-390">Структура запроса вызова *Application Insights* можно найти в этот метод также, как *URL-адрес запроса* конечной точки.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="8c2d7-391">Прямо под **FetchAnalytics()** метод, добавьте метод с именем **GetWebRequest()** , который возвращает *IEnumerator*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="8c2d7-392">Этот метод отвечает за запрос, сколько раз событие, соответствующее конкретному *GameObject*, был вызван в *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="8c2d7-393">Если все отправленные запросы вернули, **DetermineWinner()** вызывается метод.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="8c2d7-394">Далее метод **DetermineWinner()** , который сортирует список из *GameObject* и *Int* пары, в соответствии с наибольшее количество событий.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="8c2d7-395">Затем он изменяет цвет материала, *GameObject* для *зеленый* (в виде обратной связи для оно имеет наибольшие число).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="8c2d7-396">Откроется сообщение с результатами анализа.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="8c2d7-397">Добавьте структуру класса, который будет использоваться для десериализации объекта JSON, полученных от *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="8c2d7-398">Добавьте эти классы в самом низу окна вашего **DataFromAnalytics** файл класса **за пределами** определения класса.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="8c2d7-399">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="8c2d7-400">Глава 10 — создать класс перемещения</span><span class="sxs-lookup"><span data-stu-id="8c2d7-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="8c2d7-401">**Перемещения** скрипт представляет следующий скрипт, необходимо будет создать.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="8c2d7-402">Он отвечает за:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-402">It is responsible for:</span></span>

- <span data-ttu-id="8c2d7-403">Перемещение камеры Main в соответствии с направление камеры смотрит сторону.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="8c2d7-404">Добавление всех других скриптов объектов сцены.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="8c2d7-405">Для создания скрипта:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-405">To create the script:</span></span>

1.  <span data-ttu-id="8c2d7-406">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="8c2d7-407">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **создать**  >   **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="8c2d7-408">Назовите сценарий **перемещения**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="8c2d7-409">Дважды щелкните сценарий, чтобы открыть его с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="8c2d7-410">Замените существующий код следующим:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="8c2d7-411">В рамках **перемещения** класс, *ниже* пустой **Update()** метод, вставьте следующие методы, позволяющие пользователю с помощью контроллера вручную перемещать в виртуальном пространстве:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="8c2d7-412">Наконец, добавьте вызов метода в **Update()** метод.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="8c2d7-413">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="8c2d7-414">Глава 11 - Настройка ссылки на скрипты</span><span class="sxs-lookup"><span data-stu-id="8c2d7-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="8c2d7-415">В этой главе, вам потребуется разместить **перемещения** скрипт на **камеры родительского** и задайте его ссылку целевых объектов.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="8c2d7-416">Затем этот скрипт обрабатывающий размещение другие сценарии, где они должны быть.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="8c2d7-417">Из **сценарии** папку в *панель проекта*, перетащите **перемещения** сценария **камеры родительского** объект, расположенный в  *Панель иерархии*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Настройка ссылок сценариев в сцене Unity](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="8c2d7-419">Щелкните **камеры родительского**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="8c2d7-420">В *панели иерархии*, перетащите **правом** объекта из *панели иерархии* для ссылочной целевой **контроллера**в *Панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="8c2d7-421">Задайте **скорость пользователя** для **5**, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Настройка ссылок сценариев в сцене Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="8c2d7-423">Глава 12 - сборки проекта Unity</span><span class="sxs-lookup"><span data-stu-id="8c2d7-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="8c2d7-424">Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="8c2d7-425">Перейдите к **параметры сборки**, (**файл** > **параметры сборки**).</span><span class="sxs-lookup"><span data-stu-id="8c2d7-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="8c2d7-426">Из **параметры построения** окно, нажмите кнопку **построения**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Построение проекта Unity, чтобы решение универсальной платформы Windows](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="8c2d7-428">Объект **проводнике** всплывающее окно будет окно, для расположения для сборки.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="8c2d7-429">Создайте новую папку (щелкнув **новую папку** в левом верхнем углу) и назовите его **ПОСТРОЕНИЯ**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Построение проекта Unity, чтобы решение универсальной платформы Windows](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="8c2d7-431">Откройте новый **ПОСТРОЕНИЯ** папки и создайте другую папку (с помощью **новую папку** еще раз) и назовите его **MR\_Azure\_приложения\_ Insights**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Построение проекта Unity, чтобы решение универсальной платформы Windows](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="8c2d7-433">С помощью **MR\_Azure\_приложения\_Insights** щелкните папку, **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="8c2d7-434">Проекта займет около минуты для построения.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="8c2d7-435">Следуя *построения*, **проводнике** появится расположение нового проекта.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="8c2d7-436">Глава 13 - развертывание приложения MR_Azure_Application_Insights на компьютер</span><span class="sxs-lookup"><span data-stu-id="8c2d7-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="8c2d7-437">Чтобы развернуть **MR\_Azure\_приложения\_Insights** приложения на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="8c2d7-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="8c2d7-438">Откройте файл решения вашей **MR\_Azure\_приложения\_Insights** приложения в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="8c2d7-439">В **платформа решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="8c2d7-440">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Построение проекта Unity, чтобы решение универсальной платформы Windows](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="8c2d7-442">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на компьютер.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="8c2d7-443">Приложения появятся в списке установленных приложений, Готово к запуску.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="8c2d7-444">Запустите приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="8c2d7-445">Перемещение сцены, приближается к объектам и просмотрев их, когда *служба Azure Insight* собрал достаточно данных событий она будет задана объект, который достиг максимально на зеленый.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="8c2d7-446">Хотя среднего времени ожидания *событий и метрик* собираемых службой занимает около 15 минут, в некоторых случаях может занять до 1 часа.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="8c2d7-447">Глава 14 - портале службы Application Insights</span><span class="sxs-lookup"><span data-stu-id="8c2d7-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="8c2d7-448">После того как перемещаемое вокруг сцены и gazed на несколько объектов вы увидите данные, собранные в *служба Application Insights* портала.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="8c2d7-449">Вернитесь на портал службы Application Insights.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="8c2d7-450">Щелкните *обозревателя метрик*.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-450">Click on *Metrics Explorer*.</span></span>

    ![Просмотрев собранных данных](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="8c2d7-452">Она откроется на вкладке, содержащий граф, которые представляют *событий и метрик* относящиеся к приложению.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="8c2d7-453">Как упоминалось выше, может занять некоторое время (до 1 часа) для данных для отображения на графике</span><span class="sxs-lookup"><span data-stu-id="8c2d7-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Просмотрев собранных данных](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="8c2d7-455">Щелкните *строке события* в *всего событий* каждой версии приложения, чтобы просмотреть подробный разбор события со значениями их имена.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Просмотрев собранных данных](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="8c2d7-457">Ваш завершения приложения службы Application Insights</span><span class="sxs-lookup"><span data-stu-id="8c2d7-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="8c2d7-458">Поздравляем, вы создали приложение смешанной реальности, которое использует службы Application Insights для отслеживания действий пользователей в приложении.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![результат курс](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="8c2d7-460">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="8c2d7-460">Bonus Exercises</span></span>

<span data-ttu-id="8c2d7-461">**Упражнение 1**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-461">**Exercise 1**</span></span>

<span data-ttu-id="8c2d7-462">Попробуйте порождении процесса, а не вручную, создание объектов ObjectInScene и установить их координаты на плоскости в сценариях.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="8c2d7-463">Таким образом, можно также попросить Azure наиболее популярных объект был (либо из взглядом или выражение с учетом результатов) и spawn *дополнительный* одного из этих объектов.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="8c2d7-464">**Упражнение 2**</span><span class="sxs-lookup"><span data-stu-id="8c2d7-464">**Exercise 2**</span></span>

<span data-ttu-id="8c2d7-465">Чтобы отсортировать результаты Application Insights, время, чтобы получить наиболее важные данные и реализовать эти конфиденциальные данные времени в приложении.</span><span class="sxs-lookup"><span data-stu-id="8c2d7-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

