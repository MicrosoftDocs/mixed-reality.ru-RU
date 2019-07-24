---
title: MR и Azure 309 — Application Insights
description: Пройдите этот курс, чтобы узнать, как собираются аналитики в отношении поведения пользователей в приложении смешанной реальности с помощью службы Application Insights Azure.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, Application Insights, hololens, иммерсивное, VR
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694563"
---
>[!NOTE]
><span data-ttu-id="31ede-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="31ede-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="31ede-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="31ede-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="31ede-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="31ede-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="31ede-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="31ede-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="31ede-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="31ede-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="31ede-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="31ede-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="31ede-110">MR и Azure 309: Application Insights</span><span class="sxs-lookup"><span data-stu-id="31ede-110">MR and Azure 309: Application insights</span></span>

![окончательный продукт — запуск](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="31ede-112">В этом курсе вы узнаете, как добавлять Application Insights возможности в приложение смешанной реальности с помощью API Application Insights Azure для получения сведений о поведении пользователей.</span><span class="sxs-lookup"><span data-stu-id="31ede-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="31ede-113">Application Insights — это служба Майкрософт, позволяющая разработчикам получать аналитические средства из своих приложений и управлять ими с помощью простого в использовании портала.</span><span class="sxs-lookup"><span data-stu-id="31ede-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="31ede-114">Аналитика может представлять собой любое значение от производительности до настраиваемой информации, которую вы хотите получить.</span><span class="sxs-lookup"><span data-stu-id="31ede-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="31ede-115">Дополнительные сведения см. на [странице Application Insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="31ede-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="31ede-116">Прополнив этот курс, вы получите иммерсивное приложение для наушников, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="31ede-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="31ede-117">Позволяет пользователю взходить и перемещаться по сцене.</span><span class="sxs-lookup"><span data-stu-id="31ede-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="31ede-118">Активируйте отправку аналитики в *службу Application Insights*, используя взгляд и близость к объектам в сцене.</span><span class="sxs-lookup"><span data-stu-id="31ede-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="31ede-119">Приложение также будет вызывать службу, получая сведения о том, какой объект приближается к большинству пользователей, за последние 24 часа.</span><span class="sxs-lookup"><span data-stu-id="31ede-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="31ede-120">Этот объект изменит свой цвет на зеленый.</span><span class="sxs-lookup"><span data-stu-id="31ede-120">That object will change its color to green.</span></span>

<span data-ttu-id="31ede-121">В этом курсе вы узнаете, как получить результаты из службы Application Insights в примере приложения на основе Unity.</span><span class="sxs-lookup"><span data-stu-id="31ede-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="31ede-122">Вы сможете применить эти понятия к настраиваемому приложению, которое вы можете собрать.</span><span class="sxs-lookup"><span data-stu-id="31ede-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="31ede-123">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="31ede-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="31ede-124">Хождение</span><span class="sxs-lookup"><span data-stu-id="31ede-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="31ede-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="31ede-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="31ede-126"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="31ede-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="31ede-127">MR и Azure 309: Application Insights</span><span class="sxs-lookup"><span data-stu-id="31ede-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="31ede-128">✔️</span><span class="sxs-lookup"><span data-stu-id="31ede-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="31ede-129">✔️</span><span class="sxs-lookup"><span data-stu-id="31ede-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="31ede-130">Хотя этот курс в основном ориентирован на гарнитуры Windows Mixed Reality (VR), вы также можете применить сведения, которые вы узнаете в этом курсе, к Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="31ede-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="31ede-131">Как вы пройдете вместе с курсом, вы увидите примечания о любых изменениях, которые могут потребоваться для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="31ede-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="31ede-132">При использовании HoloLens вы можете заметить некоторые эхо во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="31ede-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31ede-133">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="31ede-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="31ede-134">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="31ede-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="31ede-135">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018).</span><span class="sxs-lookup"><span data-stu-id="31ede-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="31ede-136">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="31ede-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="31ede-137">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="31ede-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="31ede-138">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="31ede-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="31ede-139">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="31ede-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="31ede-140">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="31ede-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="31ede-141">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="31ede-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="31ede-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="31ede-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="31ede-143">Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="31ede-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="31ede-144">Набор наушников со встроенным микрофоном (если у гарнитуры нет встроенного микрофона и динамиков);</span><span class="sxs-lookup"><span data-stu-id="31ede-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="31ede-145">Доступ к Интернету для установки Azure и Application Insights получение данных</span><span class="sxs-lookup"><span data-stu-id="31ede-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="31ede-146">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="31ede-146">Before you start</span></span>

<span data-ttu-id="31ede-147">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="31ede-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="31ede-148">Помните, что *Application Insights* данных занимает время, поэтому подождите.</span><span class="sxs-lookup"><span data-stu-id="31ede-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="31ede-149">Если вы хотите проверить, получит ли служба ваши данные, ознакомьтесь с [главой 14](#chapter-14---the-application-insights-service-portal), в которой показано, как перемещаться по порталу.</span><span class="sxs-lookup"><span data-stu-id="31ede-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="31ede-150">Глава 1. портал Azure</span><span class="sxs-lookup"><span data-stu-id="31ede-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="31ede-151">Чтобы использовать *Application Insights*, необходимо создать и настроить *службу Application Insights* в портал Azure.</span><span class="sxs-lookup"><span data-stu-id="31ede-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="31ede-152">Войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="31ede-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="31ede-153">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="31ede-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="31ede-154">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="31ede-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="31ede-155">Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу, найдите *Application Insights*и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="31ede-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="31ede-156">Слово **New** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="31ede-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="31ede-158">На новой странице справа будет представлено описание службы *Application Insights Azure* .</span><span class="sxs-lookup"><span data-stu-id="31ede-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="31ede-159">В нижнем левом углу этой страницы нажмите кнопку **создать** , чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="31ede-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="31ede-161">После нажатия кнопки **создать**:</span><span class="sxs-lookup"><span data-stu-id="31ede-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="31ede-162">Вставьте нужное **имя** для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="31ede-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="31ede-163">В качестве **типа приложения**выберите **Общие**.</span><span class="sxs-lookup"><span data-stu-id="31ede-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="31ede-164">Выберите подходящую **подписку**.</span><span class="sxs-lookup"><span data-stu-id="31ede-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="31ede-165">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="31ede-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="31ede-166">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="31ede-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="31ede-167">Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="31ede-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="31ede-168">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="31ede-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="31ede-169">Выберите **Расположение**.</span><span class="sxs-lookup"><span data-stu-id="31ede-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="31ede-170">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="31ede-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="31ede-171">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="31ede-171">Select **Create**.</span></span>

        ![Портал Azure](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="31ede-173">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="31ede-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="31ede-174">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="31ede-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="31ede-176">Щелкните уведомления, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="31ede-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="31ede-178">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="31ede-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="31ede-179">Вы будете перенаправлены на новый экземпляр *службы Application Insights* .</span><span class="sxs-lookup"><span data-stu-id="31ede-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="31ede-181">Не открывайте эту веб-страницу и легко получайте к ней доступ. чтобы увидеть собранные данные, вы будете регулярно возвращаться.</span><span class="sxs-lookup"><span data-stu-id="31ede-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="31ede-182">Чтобы реализовать Application Insights, необходимо использовать три (3) конкретных значения: **Ключ инструментирования**, **идентификатор приложения**и **ключ API**.</span><span class="sxs-lookup"><span data-stu-id="31ede-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="31ede-183">Ниже вы узнаете, как получить эти значения из службы.</span><span class="sxs-lookup"><span data-stu-id="31ede-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="31ede-184">Обязательно запишите эти значения на пустой странице *блокнота* , так как они будут использоваться в коде в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="31ede-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="31ede-185">Чтобы найти **ключ инструментирования**, необходимо прокрутить список функций службы и выбрать пункт **свойства**. на вкладке отобразится **ключ службы**.</span><span class="sxs-lookup"><span data-stu-id="31ede-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="31ede-187">Немного ниже **свойств**вы найдете **доступ к API**, который нужно щелкнуть.</span><span class="sxs-lookup"><span data-stu-id="31ede-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="31ede-188">Панель справа предоставит **идентификатор приложения** .</span><span class="sxs-lookup"><span data-stu-id="31ede-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="31ede-190">Если панель **идентификатор приложения** все еще открыта, нажмите кнопку **создать ключ API**, которая откроет панель *создать ключ API* .</span><span class="sxs-lookup"><span data-stu-id="31ede-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Портал Azure](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="31ede-192">На панели теперь откройте *Создание ключа API* , введите описание и укажите **три поля**.</span><span class="sxs-lookup"><span data-stu-id="31ede-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="31ede-193">Нажмите кнопку **создать ключ**.</span><span class="sxs-lookup"><span data-stu-id="31ede-193">Click **Generate Key**.</span></span> <span data-ttu-id="31ede-194">Ваш **ключ API** будет создан и отображен.</span><span class="sxs-lookup"><span data-stu-id="31ede-194">Your **API Key** will be created and displayed.</span></span> 

    ![Портал Azure](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="31ede-196">Это единственный момент, когда ваш **ключ службы** будет отображаться, поэтому убедитесь, что вы создали его копию.</span><span class="sxs-lookup"><span data-stu-id="31ede-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="31ede-197">Глава 2. Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="31ede-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="31ede-198">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="31ede-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="31ede-199">Откройте *Unity* и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="31ede-199">Open *Unity* and click **New**.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="31ede-201">Теперь необходимо указать имя проекта Unity, а затем вставить **MR\_Azure\_Application\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="31ede-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="31ede-202">Убедитесь, что для *шаблона* задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="31ede-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="31ede-203">Задайте для *расположения нужное расположение* (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="31ede-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="31ede-204">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="31ede-204">Then, click **Create project**.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="31ede-206">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="31ede-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="31ede-207">Перейдите к разделу **изменение \> настроек** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="31ede-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="31ede-208">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="31ede-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="31ede-209">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="31ede-209">Close the **Preferences** window.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="31ede-211">Затем перейдите в раздел **Параметры \> сборки файлов** и переключите платформу на **универсальная платформа Windows**, нажав кнопку коммутатора на **платформе** .</span><span class="sxs-lookup"><span data-stu-id="31ede-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="31ede-213">Перейдите в **раздел \> параметры сборки файлов** и убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="31ede-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="31ede-214">**Целевое устройство** настроено для **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="31ede-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="31ede-215">Для Microsoft HoloLens задайте для параметра **целевое устройство** значение *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="31ede-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="31ede-216">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="31ede-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="31ede-217">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="31ede-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="31ede-218">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="31ede-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="31ede-219">Сохраните сцену и добавьте ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="31ede-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="31ede-220">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="31ede-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="31ede-221">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="31ede-221">A save window will appear.</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="31ede-223">Создайте новую папку для этой и любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее **сцены**.</span><span class="sxs-lookup"><span data-stu-id="31ede-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="31ede-225">Откройте только что созданную папку **сцены** , а затем в поле *имя файла:* введите **аппликатионинсигхтссцене**, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="31ede-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="31ede-227">Оставшиеся параметры, в **параметрах сборки**, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="31ede-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="31ede-228">В окне **параметры сборки** нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится **инспектор** .</span><span class="sxs-lookup"><span data-stu-id="31ede-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="31ede-230">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="31ede-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="31ede-231">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="31ede-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="31ede-232">**Создание сценариев** **Версия среды выполнения** должна быть **экспериментальной (эквивалент .NET 4,6)** , что вызовет необходимость перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="31ede-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="31ede-233">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="31ede-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="31ede-234">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="31ede-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="31ede-236">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="31ede-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="31ede-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="31ede-237">**InternetClient**</span></span>     

            ![Настройка проекта Unity](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="31ede-239">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="31ede-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="31ede-241">Вернувшись в **параметры сборки**, **проекты C# Unity** больше не заключаются. Установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="31ede-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="31ede-242">Закройте окно параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="31ede-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="31ede-243">Сохраните сцену и проект (**файл** > **сохранить сцену/файл** > **сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="31ede-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="31ede-244">Глава 3. Импорт пакета Unity</span><span class="sxs-lookup"><span data-stu-id="31ede-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31ede-245">Если вы хотите пропустить *настройку Unity* , настроили компоненты этого курса, и продолжить работу с кодом, скачайте этот пакет [Azure-MR-309. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), импортируйте его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="31ede-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="31ede-246">Это также будет содержать библиотеки DLL из следующей главы.</span><span class="sxs-lookup"><span data-stu-id="31ede-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="31ede-247">После импорта продолжите работу в [**главе 6**](#chapter-6---create-the-applicationinsightstracker-class).</span><span class="sxs-lookup"><span data-stu-id="31ede-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31ede-248">Чтобы использовать Application Insights в Unity, необходимо импортировать библиотеку DLL для нее вместе с библиотекой DLL Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="31ede-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="31ede-249">В Unity существует известная ошибка, которая требует перенастройки подключаемых модулей после импорта.</span><span class="sxs-lookup"><span data-stu-id="31ede-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="31ede-250">Эти действия (4-7 в этом разделе) больше не понадобятся после устранения ошибки.</span><span class="sxs-lookup"><span data-stu-id="31ede-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="31ede-251">Чтобы импортировать Application Insights в свой проект, убедитесь, что вы скачали файл [". пакет unitypackage", содержащий подключаемые модули](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="31ede-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="31ede-252">Затем выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="31ede-252">Then, do the following:</span></span>

1.  <span data-ttu-id="31ede-253">Добавьте **. пакет unitypackage** в Unity с помощью команды меню  **\> \> настраиваемый пакет импорт активов** .</span><span class="sxs-lookup"><span data-stu-id="31ede-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="31ede-254">В появившемся окне **Импорт пакета Unity** убедитесь, что выбраны все компоненты **подключаемых модулей** (включая).</span><span class="sxs-lookup"><span data-stu-id="31ede-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="31ede-256">Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="31ede-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="31ede-257">Перейдите в папку **Insights** в разделе **подключаемые модули** в представлении проекта и выберите *только*следующие подключаемые модули:</span><span class="sxs-lookup"><span data-stu-id="31ede-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="31ede-258">Microsoft. ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="31ede-258">Microsoft.ApplicationInsights</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="31ede-260">Выбрав этот *подключаемый модуль* , убедитесь, что **все платформы** **не установлены**, убедитесь, что флажок **всаплайер** также не **установлен**, а затем нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="31ede-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="31ede-261">Для этого нужно убедиться, что файлы настроены правильно.</span><span class="sxs-lookup"><span data-stu-id="31ede-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="31ede-263">Пометив подключаемые модули подобным образом, настройте их для использования только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="31ede-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="31ede-264">В папке WSA имеется другой набор библиотек DLL, который будет использоваться после экспорта проекта из Unity.</span><span class="sxs-lookup"><span data-stu-id="31ede-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="31ede-265">Далее необходимо открыть папку **WSA** в папке **Insights** .</span><span class="sxs-lookup"><span data-stu-id="31ede-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="31ede-266">Вы увидите копию того же файла, который вы только что настроили.</span><span class="sxs-lookup"><span data-stu-id="31ede-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="31ede-267">Выберите этот файл, а затем в инспекторе убедитесь, что **все платформы** не установлены, убедитесь, что **установлен**флажок **только** **всаплайер** .</span><span class="sxs-lookup"><span data-stu-id="31ede-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="31ede-268">Щелкните **Применить**.</span><span class="sxs-lookup"><span data-stu-id="31ede-268">Click **Apply**.</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="31ede-270">Теперь необходимо выполнить **шаги 4-6**, но для подключаемых модулей *Newtonsoft* .</span><span class="sxs-lookup"><span data-stu-id="31ede-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="31ede-271">На снимке экрана ниже показано, как должен выглядеть результат.</span><span class="sxs-lookup"><span data-stu-id="31ede-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Импорт пакета Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="31ede-273">Глава 4. Настройка камеры и пользовательских элементов управления</span><span class="sxs-lookup"><span data-stu-id="31ede-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="31ede-274">В этой главе будет настроена камера и элементы управления, позволяющие пользователю просматривать и перемещать сцену.</span><span class="sxs-lookup"><span data-stu-id="31ede-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="31ede-275">Щелкните правой кнопкой мыши пустую область на панели Иерархия, а затем в поле **создать** > **пустое**.</span><span class="sxs-lookup"><span data-stu-id="31ede-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="31ede-277">Переименуйте новый пустой GameObject в **родительский элемент Camera**.</span><span class="sxs-lookup"><span data-stu-id="31ede-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="31ede-279">Щелкните правой кнопкой мыши пустую область на панели Иерархия, затем на **трехмерном объекте**, а затем в **сфере**.</span><span class="sxs-lookup"><span data-stu-id="31ede-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="31ede-280">Переименуйте сферу в **правой части**.</span><span class="sxs-lookup"><span data-stu-id="31ede-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="31ede-281">Задайте **Масштаб преобразования** правой части в **0,1, 0,1, 0,1**</span><span class="sxs-lookup"><span data-stu-id="31ede-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="31ede-283">Удалите компонент "Сфера" **сферы Sphere** с правой стороны, щелкнув **шестеренку** в компоненте "Сфера" *сферы* , а затем **удалив компонент**.</span><span class="sxs-lookup"><span data-stu-id="31ede-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="31ede-285">На панели Иерархия перетащите **основную камеру** и **правой рукой** объекты на родительский объект **Camera** .</span><span class="sxs-lookup"><span data-stu-id="31ede-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="31ede-287">Задайте для параметра **Расположение преобразования** как для **основной камеры** , так и для **правой стороны** объекта значение **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="31ede-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-31.png)

    ![Настройка камеры и пользовательских элементов управления](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="31ede-290">Глава 5. Настройка объектов в сцене Unity</span><span class="sxs-lookup"><span data-stu-id="31ede-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="31ede-291">Теперь вы создадите базовые фигуры для сцены, с которыми может взаимодействовать пользователь.</span><span class="sxs-lookup"><span data-stu-id="31ede-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="31ede-292">Щелкните правой кнопкой мыши пустую область на *панели Иерархия*, затем на **трехмерном объекте**, а затем выберите **плоскость**.</span><span class="sxs-lookup"><span data-stu-id="31ede-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="31ede-293">Установите для параметра **Расположение преобразования** плоскости значение **0,-1, 0**.</span><span class="sxs-lookup"><span data-stu-id="31ede-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="31ede-294">Установите шкалу **преобразования** плоскости в значение **5, 1, 5**.</span><span class="sxs-lookup"><span data-stu-id="31ede-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="31ede-296">Создайте базовый материал для использования с объектом **плоскости** , чтобы сделать другие фигуры более удобными для просмотра.</span><span class="sxs-lookup"><span data-stu-id="31ede-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="31ede-297">Перейдите на *Панель проекта*, щелкните правой кнопкой мыши, а затем выберите **создать**, а затем — **Папка**, чтобы создать новую папку.</span><span class="sxs-lookup"><span data-stu-id="31ede-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="31ede-298">Назовите **материалы**IT.</span><span class="sxs-lookup"><span data-stu-id="31ede-298">Name it **Materials**.</span></span>

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-34.png) ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="31ede-301">Откройте папку **материалы** , щелкните правой кнопкой мыши, выберите **создать**, а затем — **материал**, чтобы создать новый материал.</span><span class="sxs-lookup"><span data-stu-id="31ede-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="31ede-302">Назовите его **Blue**.</span><span class="sxs-lookup"><span data-stu-id="31ede-302">Name it **Blue**.</span></span>

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-36.png) ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="31ede-305">Выбрав новый **синий** материал, Взгляните на *инспектор*и щелкните прямоугольное окно рядом с **албедо**.</span><span class="sxs-lookup"><span data-stu-id="31ede-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="31ede-306">Выберите синий цвет (один рисунок имеет **шестнадцатеричный цвет: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="31ede-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="31ede-307">После выбора нажмите кнопку Закрыть.</span><span class="sxs-lookup"><span data-stu-id="31ede-307">Click the close button once you have chosen.</span></span>

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="31ede-309">Перетащите новый материал из папки **материалы** в созданную **плоскость**на сцене (или перетащите ее на объект **плоскости** в *иерархии*).</span><span class="sxs-lookup"><span data-stu-id="31ede-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="31ede-311">Щелкните правой кнопкой мыши пустую область на *панели Иерархия*, а затем на **трехмерном объекте, капсула**.</span><span class="sxs-lookup"><span data-stu-id="31ede-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="31ede-312">Выбрав капсулу, **измените ее** *Расположение* на: **-10, 1, 0**.</span><span class="sxs-lookup"><span data-stu-id="31ede-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="31ede-313">Щелкните правой кнопкой мыши пустую область на *панели Иерархия*, а затем выберите **трехмерный объект куб**.</span><span class="sxs-lookup"><span data-stu-id="31ede-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="31ede-314">Выбрав **куб** , измените его *Расположение* **преобразования** на: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="31ede-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="31ede-315">Щелкните правой кнопкой мыши пустую область на *панели Иерархия*, а затем на **трехмерном объекте, Sphere**.</span><span class="sxs-lookup"><span data-stu-id="31ede-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="31ede-316">Выбрав сферу, **измените ее** *Расположение* на:  **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="31ede-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="31ede-318">Эти значения *позиций* являются *предложениями*.</span><span class="sxs-lookup"><span data-stu-id="31ede-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="31ede-319">Вы можете устанавливать позиции объектов в соответствии с любыми требованиями, хотя это и проще для пользователей приложения, если расстояния между объектами не слишком далеко от камеры.</span><span class="sxs-lookup"><span data-stu-id="31ede-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="31ede-320">Когда приложение работает, оно должно иметь возможность определять объекты в сцене, чтобы добиться этого, они должны быть помечены тегами.</span><span class="sxs-lookup"><span data-stu-id="31ede-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="31ede-321">Выберите один из объектов и на панели инспектора  щелкните **Добавить тег...** , который заменит *инспектор* **тегами & слоями** .</span><span class="sxs-lookup"><span data-stu-id="31ede-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="31ede-322">![Настройка объектов в сцене](images/AzureLabs-Lab309-41.png) Unity![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="31ede-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="31ede-323">Щелкните символ **+ (плюс)** , а затем введите имя тега **обжектинсцене**.</span><span class="sxs-lookup"><span data-stu-id="31ede-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Настройка объектов в сцене Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="31ede-325">Если вы используете другое имя для тега, необходимо убедиться, что это изменение также стало *датафроманалитикс*, *обжекттригжер*и скриптом позже, чтобы объекты были найдены и обнаружены в сцене.</span><span class="sxs-lookup"><span data-stu-id="31ede-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="31ede-326">Теперь, когда тег создан, необходимо применить его ко всем трем объектам.</span><span class="sxs-lookup"><span data-stu-id="31ede-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="31ede-327">В *иерархии*удерживайте клавишу **SHIFT** , затем щелкните капсулу,  **куб**и сферу, объекты, затем в инспекторе щелкните раскрывающееся меню рядом с **тегом**, а затем щелкните *обжектинсцене* созданный тег.</span><span class="sxs-lookup"><span data-stu-id="31ede-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="31ede-328">![Настройка объектов в сцене](images/AzureLabs-Lab309-44.png) Unity![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="31ede-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="31ede-329">Глава 6. Создание класса Аппликатионинсигхтстраккер</span><span class="sxs-lookup"><span data-stu-id="31ede-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="31ede-330">Первый скрипт, который необходимо создать, — это **аппликатионинсигхтстраккер**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="31ede-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="31ede-331">Создание событий на основе взаимодействия пользователя для отправки в Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="31ede-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="31ede-332">Создание подходящих имен событий в зависимости от взаимодействия с пользователем.</span><span class="sxs-lookup"><span data-stu-id="31ede-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="31ede-333">Отправка событий в экземпляр службы Application Insights.</span><span class="sxs-lookup"><span data-stu-id="31ede-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="31ede-334">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="31ede-334">To create this class:</span></span>

1.  <span data-ttu-id="31ede-335">Щелкните правой кнопкой мыши на *панели проект*, а затем выберите **создать** > **папку**.</span><span class="sxs-lookup"><span data-stu-id="31ede-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="31ede-336">Назовите папку **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="31ede-336">Name the folder **Scripts**.</span></span>

    ![Создание класса Аппликатионинсигхтстраккер](images/AzureLabs-Lab309-46.png)  ![Создание класса Аппликатионинсигхтстраккер](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="31ede-339">После создания  папки Scripts (скрипты) дважды щелкните ее, чтобы открыть.</span><span class="sxs-lookup"><span data-stu-id="31ede-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="31ede-340">Затем в этой папке щелкните правой кнопкой мыши пункт **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="31ede-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="31ede-341">Назовите сценарий **аппликатионинсигхтстраккер**.</span><span class="sxs-lookup"><span data-stu-id="31ede-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="31ede-342">Дважды щелкните новый скрипт **аппликатионинсигхтстраккер** , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="31ede-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="31ede-343">Обновите пространства имен в верхней части скрипта следующим образом:</span><span class="sxs-lookup"><span data-stu-id="31ede-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="31ede-344">Внутри класса вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="31ede-344">Inside the class insert the following variables:</span></span>

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
    > <span data-ttu-id="31ede-345">Задайте соответствующие значения **instrumentationKey, applicationId и API_Key** , используя *ключи службы* на портале Azure, как упоминалось в [главе 1](#chapter-1---the-azure-portal), шаг 9.</span><span class="sxs-lookup"><span data-stu-id="31ede-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="31ede-346">Затем добавьте методы **Start ()** и **спящего режима ()** , которые будут вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="31ede-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="31ede-347">Добавьте методы, отвечающие за отправку событий и метрик, зарегистрированных в приложении:</span><span class="sxs-lookup"><span data-stu-id="31ede-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

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

8.  <span data-ttu-id="31ede-348">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="31ede-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="31ede-349">Глава 7. Создание скрипта «взгляд»</span><span class="sxs-lookup"><span data-stu-id="31ede-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="31ede-350">Следующий скрипт для создания — это скрипт « **взгляд** ».</span><span class="sxs-lookup"><span data-stu-id="31ede-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="31ede-351">Этот сценарий отвечает за создание *райкаст* , который будет проецирован вперед с *основной камеры*для определения объекта, на котором пользователь смотрит.</span><span class="sxs-lookup"><span data-stu-id="31ede-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="31ede-352">В этом случае *райкаст* должен выяснить, просматривает ли пользователь объект с тегом **обжектинсцене** , а затем подсчитать, как *долго пользователь смотрит* на этот объект.</span><span class="sxs-lookup"><span data-stu-id="31ede-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="31ede-353">Дважды щелкните папку Scripts  , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="31ede-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="31ede-354">Щелкните правой кнопкой мыши внутри  папки Scripts и выберите команду **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="31ede-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="31ede-355">Присвойте скрипту имя « **взгляд**».</span><span class="sxs-lookup"><span data-stu-id="31ede-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="31ede-356">Дважды щелкните скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31ede-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="31ede-357">Замените существующий код следующим:</span><span class="sxs-lookup"><span data-stu-id="31ede-357">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="31ede-358">Теперь необходимо добавить код для методов спящего режима **()** и **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="31ede-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

6.  <span data-ttu-id="31ede-359">В классе **взгляд** добавьте следующий код в метод **Update ()** для проецирования *райкаст* и обнаружения попадания целевого объекта:</span><span class="sxs-lookup"><span data-stu-id="31ede-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

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

7.  <span data-ttu-id="31ede-360">Добавьте метод **ресетфокуседобжект ()** для отправки данных в **Application Insights** , когда пользователь просматривает объект.</span><span class="sxs-lookup"><span data-stu-id="31ede-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

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

8.  <span data-ttu-id="31ede-361">Вы завершили выполнение скрипта " **взгляд** ".</span><span class="sxs-lookup"><span data-stu-id="31ede-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="31ede-362">Сохраните изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="31ede-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="31ede-363">Глава 8. Создание класса Обжекттригжер</span><span class="sxs-lookup"><span data-stu-id="31ede-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="31ede-364">Следующий сценарий, который необходимо создать, — это **обжекттригжер**, который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="31ede-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="31ede-365">Добавление компонентов, необходимых для конфликта на основной камере.</span><span class="sxs-lookup"><span data-stu-id="31ede-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="31ede-366">Обнаружение того, приближается ли камера к объекту, помеченному как **обжектинсцене**.</span><span class="sxs-lookup"><span data-stu-id="31ede-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="31ede-367">Чтобы создать скрипт, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="31ede-367">To create the script:</span></span>

1.  <span data-ttu-id="31ede-368">Дважды щелкните папку Scripts  , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="31ede-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="31ede-369">Щелкните правой кнопкой мыши внутри  папки Scripts и выберите команду **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="31ede-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="31ede-370">Назовите сценарий **обжекттригжер**.</span><span class="sxs-lookup"><span data-stu-id="31ede-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="31ede-371">Дважды щелкните скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31ede-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="31ede-372">Замените существующий код следующим:</span><span class="sxs-lookup"><span data-stu-id="31ede-372">Replace the existing code with the following:</span></span>

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

4.  <span data-ttu-id="31ede-373">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="31ede-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="31ede-374">Глава 9. Создание класса Датафроманалитикс</span><span class="sxs-lookup"><span data-stu-id="31ede-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="31ede-375">Теперь необходимо создать скрипт **датафроманалитикс** , который отвечает за:</span><span class="sxs-lookup"><span data-stu-id="31ede-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="31ede-376">Получение данных аналитики о том, какой объект использовался камерой в большинстве случаев.</span><span class="sxs-lookup"><span data-stu-id="31ede-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="31ede-377">С помощью *ключей службы*, которые позволяют обмениваться данными с экземпляром службы Application Insights Azure.</span><span class="sxs-lookup"><span data-stu-id="31ede-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="31ede-378">Сортировка объектов в сцене в соответствии с наибольшим числом событий.</span><span class="sxs-lookup"><span data-stu-id="31ede-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="31ede-379">Изменение цвета материала наиболее приближенного объекта на *зеленый*.</span><span class="sxs-lookup"><span data-stu-id="31ede-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="31ede-380">Чтобы создать скрипт, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="31ede-380">To create the script:</span></span>

1.  <span data-ttu-id="31ede-381">Дважды щелкните папку Scripts  , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="31ede-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="31ede-382">Щелкните правой кнопкой мыши внутри  папки Scripts и выберите команду **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="31ede-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="31ede-383">Назовите сценарий **датафроманалитикс**.</span><span class="sxs-lookup"><span data-stu-id="31ede-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="31ede-384">Дважды щелкните скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31ede-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="31ede-385">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="31ede-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="31ede-386">Внутри скрипта вставьте следующее:</span><span class="sxs-lookup"><span data-stu-id="31ede-386">Inside the script, insert the following:</span></span>

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

6.  <span data-ttu-id="31ede-387">В классе **датафроманалитикс** сразу после метода **Start ()** добавьте следующий метод с именем **фетчаналитикс ()** .</span><span class="sxs-lookup"><span data-stu-id="31ede-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="31ede-388">Этот метод отвечает за заполнение списка пар "ключ-значение" с помощью *GameObject* и количества заполнительных счетчиков событий.</span><span class="sxs-lookup"><span data-stu-id="31ede-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="31ede-389">Затем он инициализирует соподпрограмму **жетвебрекуест ()** .</span><span class="sxs-lookup"><span data-stu-id="31ede-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="31ede-390">Структура запроса вызова *Application Insights* можно найти в этом методе также в качестве конечной точки *URL-адреса запроса* .</span><span class="sxs-lookup"><span data-stu-id="31ede-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

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

7.  <span data-ttu-id="31ede-391">Непосредственно под методом **фетчаналитикс ()** добавьте метод с именем **жетвебрекуест ()** , который возвращает *IEnumerator*.</span><span class="sxs-lookup"><span data-stu-id="31ede-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="31ede-392">Этот метод отвечает за запрос числа вызовов события, соответствующего определенному *GameObject*, в *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="31ede-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="31ede-393">Когда возвращаются все отправленные запросы, вызывается метод **детерминевиннер ()** .</span><span class="sxs-lookup"><span data-stu-id="31ede-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

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

8.  <span data-ttu-id="31ede-394">Следующий метод — **детерминевиннер ()** , который сортирует список пар *GameObject* и *int* в соответствии с наибольшим числом событий.</span><span class="sxs-lookup"><span data-stu-id="31ede-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="31ede-395">Затем он изменяет цвет материала *GameObject* на *зеленый* (в виде обратной связи с наибольшим числом).</span><span class="sxs-lookup"><span data-stu-id="31ede-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="31ede-396">Отобразится сообщение с результатами аналитики.</span><span class="sxs-lookup"><span data-stu-id="31ede-396">This displays a message with the analytics results.</span></span>

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

9.  <span data-ttu-id="31ede-397">Добавьте структуру класса, которая будет использоваться для десериализации объекта JSON, полученного от *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="31ede-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="31ede-398">Добавьте эти классы в самом низу файла класса **датафроманалитикс** **за** пределами определения класса.</span><span class="sxs-lookup"><span data-stu-id="31ede-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

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

10. <span data-ttu-id="31ede-399">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="31ede-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="31ede-400">Глава 10. Создание класса перемещения</span><span class="sxs-lookup"><span data-stu-id="31ede-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="31ede-401">Сценарий **перемещения** — это следующий скрипт, который потребуется создать.</span><span class="sxs-lookup"><span data-stu-id="31ede-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="31ede-402">Он отвечает за следующее:</span><span class="sxs-lookup"><span data-stu-id="31ede-402">It is responsible for:</span></span>

- <span data-ttu-id="31ede-403">Перемещение основной камеры в соответствии с направлением, которое ищет камера.</span><span class="sxs-lookup"><span data-stu-id="31ede-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="31ede-404">Добавление всех других скриптов в объекты сцены.</span><span class="sxs-lookup"><span data-stu-id="31ede-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="31ede-405">Чтобы создать скрипт, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="31ede-405">To create the script:</span></span>

1.  <span data-ttu-id="31ede-406">Дважды щелкните папку Scripts  , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="31ede-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="31ede-407">Щелкните правой кнопкой мыши внутри  папки Scripts и выберите команду **создать**  >   **C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="31ede-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="31ede-408">Назовите **Перемещение**скрипта.</span><span class="sxs-lookup"><span data-stu-id="31ede-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="31ede-409">Дважды щелкните скрипт, чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="31ede-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="31ede-410">Замените существующий код следующим:</span><span class="sxs-lookup"><span data-stu-id="31ede-410">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="31ede-411">В классе **перемещения** *ниже* пустого метода **Update ()** вставьте следующие методы, позволяющие пользователю использовать контроллер руки для перемещения в виртуальном пространстве:</span><span class="sxs-lookup"><span data-stu-id="31ede-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

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

6.  <span data-ttu-id="31ede-412">Наконец, добавьте вызов метода в метод **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="31ede-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="31ede-413">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="31ede-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="31ede-414">Глава 11. Настройка ссылок на скрипты</span><span class="sxs-lookup"><span data-stu-id="31ede-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="31ede-415">В этой главе необходимо поместить скрипт **перемещения** на **родительский объект камеры** и задать его ссылки на целевые объекты.</span><span class="sxs-lookup"><span data-stu-id="31ede-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="31ede-416">Затем этот скрипт будет обрабатывать размещение других сценариев, где они должны быть.</span><span class="sxs-lookup"><span data-stu-id="31ede-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="31ede-417">В папке **скрипты** на *панели проекта*перетащите скрипт **перемещения** в родительский объект **Camera** , расположенный на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="31ede-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Настройка ссылок на скрипты в сцене Unity](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="31ede-419">Щелкните родительский **элемент камеры**.</span><span class="sxs-lookup"><span data-stu-id="31ede-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="31ede-420">На *панели Иерархия*перетащите **правой кнопкой мыши** объект, расположенный на *панели Иерархия* , на целевой объект ссылки, **контроллер**и на *панели инспектора*.</span><span class="sxs-lookup"><span data-stu-id="31ede-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="31ede-421">Задайте для параметра **скорость пользователя** значение **5**, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="31ede-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Настройка ссылок на скрипты в сцене Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="31ede-423">Глава 12. Создание проекта Unity</span><span class="sxs-lookup"><span data-stu-id="31ede-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="31ede-424">Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.</span><span class="sxs-lookup"><span data-stu-id="31ede-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="31ede-425">Перейдите к **параметрам сборки**, (**параметры сборки** **файлов** > ).</span><span class="sxs-lookup"><span data-stu-id="31ede-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="31ede-426">В окне " **параметры сборки** " щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="31ede-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Создание проекта Unity для решения UWP](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="31ede-428">Откроется окно **проводника** , в котором будет предложено ввести расположение для сборки.</span><span class="sxs-lookup"><span data-stu-id="31ede-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="31ede-429">Создайте новую папку (щелкнув **создать папку** в левом верхнем углу) и назовите ее **Build**.</span><span class="sxs-lookup"><span data-stu-id="31ede-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Создание проекта Unity для решения UWP](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="31ede-431">Откройте папку " **новые сборки** " и создайте другую папку (с помощью **новой папки** еще раз) и назовите ее " **\_MR\_\_Azure Application Insights**".</span><span class="sxs-lookup"><span data-stu-id="31ede-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Создание проекта Unity для решения UWP](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="31ede-433">Выбрав папку **"\_MR\_Azure\_Application Insights** ", щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="31ede-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="31ede-434">Построение проекта займет около минуты.</span><span class="sxs-lookup"><span data-stu-id="31ede-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="31ede-435">После *сборки*появится **окно проводника** , в котором отображается расположение нового проекта.</span><span class="sxs-lookup"><span data-stu-id="31ede-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="31ede-436">Глава 13. Развертывание приложения MR_Azure_Application_Insights на компьютере</span><span class="sxs-lookup"><span data-stu-id="31ede-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="31ede-437">Чтобы развернуть приложение **MR\_Azure\_Application\_Insights** на локальном компьютере, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="31ede-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="31ede-438">Откройте файл решения для приложения **\_MR Azure\_Application\_Insights** в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="31ede-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="31ede-439">На **платформе решения**выберите **x86, локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="31ede-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="31ede-440">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="31ede-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Создание проекта Unity для решения UWP](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="31ede-442">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение на компьютере.</span><span class="sxs-lookup"><span data-stu-id="31ede-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="31ede-443">Теперь приложение должно отобразиться в списке установленных приложений, готовых к запуску.</span><span class="sxs-lookup"><span data-stu-id="31ede-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="31ede-444">Запустите приложение Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="31ede-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="31ede-445">Перемещайтесь по сцене, приближению к объектам и просматривая их, когда *служба Azure Insights* собрала достаточно данных событий, она настроит объект, который приближается к зеленому.</span><span class="sxs-lookup"><span data-stu-id="31ede-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="31ede-446">Хотя среднее время ожидания *событий и метрик* , собираемых службой, занимает около 15 минут, в некоторых случаях может потребоваться до 1 часа.</span><span class="sxs-lookup"><span data-stu-id="31ede-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="31ede-447">Глава 14. Портал службы Application Insights</span><span class="sxs-lookup"><span data-stu-id="31ede-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="31ede-448">После перемещения по сцене и газед на нескольких объектах можно просмотреть данные, собранные на портале *службы Application Insights* .</span><span class="sxs-lookup"><span data-stu-id="31ede-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="31ede-449">Вернитесь на портал службы Application Insights.</span><span class="sxs-lookup"><span data-stu-id="31ede-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="31ede-450">Щелкните *Обозреватель метрик*.</span><span class="sxs-lookup"><span data-stu-id="31ede-450">Click on *Metrics Explorer*.</span></span>

    ![Просмотр собранных данных](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="31ede-452">Он откроется на вкладке, содержащей граф, который представляет *события и метрики* , связанные с приложением.</span><span class="sxs-lookup"><span data-stu-id="31ede-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="31ede-453">Как упоминалось выше, для отображения данных на диаграмме может потребоваться некоторое время (до 1 часа).</span><span class="sxs-lookup"><span data-stu-id="31ede-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Просмотр собранных данных](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="31ede-455">Щелкните *строку событий* в *общем количестве событий* по версии приложения, чтобы просмотреть подробное разбиение событий с их именами.</span><span class="sxs-lookup"><span data-stu-id="31ede-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Просмотр собранных данных](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="31ede-457">Завершенное приложение службы Application Insights</span><span class="sxs-lookup"><span data-stu-id="31ede-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="31ede-458">Поздравляем, вы создали приложение смешанной реальности, которое использует службу Application Insights для мониторинга активности пользователей в приложении.</span><span class="sxs-lookup"><span data-stu-id="31ede-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![результат курса](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="31ede-460">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="31ede-460">Bonus Exercises</span></span>

<span data-ttu-id="31ede-461">**Упражнение 1**</span><span class="sxs-lookup"><span data-stu-id="31ede-461">**Exercise 1**</span></span>

<span data-ttu-id="31ede-462">Постарайтесь попытаться создать, а не вручную создавать объекты Обжектинсцене и задать их координаты на плоскости в скриптах.</span><span class="sxs-lookup"><span data-stu-id="31ede-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="31ede-463">Таким образом, можно попросить Azure о том, какой из наиболее популярных объектов был (из результатов поиска или взгляда), и порождать *еще* один из этих объектов.</span><span class="sxs-lookup"><span data-stu-id="31ede-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="31ede-464">**Упражнение 2**</span><span class="sxs-lookup"><span data-stu-id="31ede-464">**Exercise 2**</span></span>

<span data-ttu-id="31ede-465">Отсортируйте результаты Application Insights по времени, чтобы получить наиболее актуальные данные и реализовать эти данные, учитывающие время, в приложении.</span><span class="sxs-lookup"><span data-stu-id="31ede-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

