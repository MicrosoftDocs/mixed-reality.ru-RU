---
title: MR и Azure 307 — машинное обучение
description: Пройдите этот курс, чтобы узнать, как реализовать Машинное обучение Azure Studio в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, машинное обучение, ML, студия машинного обучения, hololens, иммерсивное, VR
ms.openlocfilehash: e302e287049cd746a436904c2af2bcc2b0835796
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926620"
---
>[!NOTE]
><span data-ttu-id="00f80-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="00f80-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="00f80-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="00f80-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="00f80-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="00f80-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="00f80-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="00f80-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="00f80-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="00f80-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="00f80-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="00f80-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="00f80-110">MR и Azure 307: машинное обучение</span><span class="sxs-lookup"><span data-stu-id="00f80-110">MR and Azure 307: Machine learning</span></span>

![окончательный продукт — запуск](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="00f80-112">В этом курсе вы узнаете, как добавить возможности Машинное обучение (машинного обучения) в приложение смешанной реальности с помощью Машинное обучение Azure Studio.</span><span class="sxs-lookup"><span data-stu-id="00f80-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="00f80-113">*Машинное обучение Azure Studio* — это служба Майкрософт, которая предоставляет разработчикам большое количество алгоритмов машинного обучения, которые могут помочь в вводе, выводе, подготовке и визуализации данных.</span><span class="sxs-lookup"><span data-stu-id="00f80-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="00f80-114">После этих компонентов можно разработать эксперимент прогнозной аналитики, выполнить его итерацию и использовать для обучения модели.</span><span class="sxs-lookup"><span data-stu-id="00f80-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="00f80-115">После обучения можно сделать модель рабочей в облаке Azure, чтобы она могла затем оценить новые данные.</span><span class="sxs-lookup"><span data-stu-id="00f80-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="00f80-116">Дополнительные сведения см. на [странице машинное обучение Azure Studio](https://azure.microsoft.com/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="00f80-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/services/machine-learning-studio/).</span></span>

<span data-ttu-id="00f80-117">Прополнив этот курс, вы получите иммерсивное приложение для наушников смешанной реальности и узнаете, как сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="00f80-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="00f80-118">Предоставьте таблицу данных о продажах на портале *машинное обучение Azure Studio* и создайте алгоритм для прогнозирования будущих продаж популярных элементов.</span><span class="sxs-lookup"><span data-stu-id="00f80-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="00f80-119">Создайте **проект Unity**, который может принимать и интерпретировать данные прогноза из службы ml.</span><span class="sxs-lookup"><span data-stu-id="00f80-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="00f80-120">Визуально отображать данные затенения в **проекте Unity**, предоставляя наиболее популярные элементы продаж на полке.</span><span class="sxs-lookup"><span data-stu-id="00f80-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="00f80-121">В приложении вы будете выполнять интеграцию результатов с вашей структурой.</span><span class="sxs-lookup"><span data-stu-id="00f80-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="00f80-122">Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="00f80-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="00f80-123">Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="00f80-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="00f80-124">Этот курс является автономным учебником, который не участвует в других практических занятиях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="00f80-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="00f80-125">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="00f80-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="00f80-126">Хождение</span><span class="sxs-lookup"><span data-stu-id="00f80-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="00f80-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="00f80-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="00f80-128"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="00f80-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="00f80-129">MR и Azure 307: машинное обучение</span><span class="sxs-lookup"><span data-stu-id="00f80-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="00f80-130">✔️</span><span class="sxs-lookup"><span data-stu-id="00f80-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="00f80-131">✔️</span><span class="sxs-lookup"><span data-stu-id="00f80-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="00f80-132">Хотя этот курс в основном ориентирован на гарнитуры Windows Mixed Reality (VR), вы также можете применить сведения, которые вы узнаете в этом курсе, к Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="00f80-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="00f80-133">Как вы пройдете вместе с курсом, вы увидите примечания о любых изменениях, которые могут потребоваться для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="00f80-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="00f80-134">При использовании HoloLens вы можете заметить некоторые эхо во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="00f80-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00f80-135">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="00f80-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="00f80-136">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="00f80-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="00f80-137">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018).</span><span class="sxs-lookup"><span data-stu-id="00f80-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="00f80-138">Вы можете использовать новейшее программное обеспечение, как указано в [статье Установка средств](install-the-tools.md), но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.</span><span class="sxs-lookup"><span data-stu-id="00f80-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="00f80-139">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="00f80-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="00f80-140">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="00f80-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="00f80-141">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="00f80-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="00f80-142">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="00f80-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="00f80-143">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="00f80-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="00f80-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="00f80-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="00f80-145">Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="00f80-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="00f80-146">Доступ к Интернету для установки Azure и получения данных машинного обучения</span><span class="sxs-lookup"><span data-stu-id="00f80-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="00f80-147">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="00f80-147">Before you start</span></span>

<span data-ttu-id="00f80-148">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="00f80-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="00f80-149">Глава 1. Настройка учетной записи хранения Azure</span><span class="sxs-lookup"><span data-stu-id="00f80-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="00f80-150">Чтобы использовать API-интерфейс Azure Translator, необходимо настроить экземпляр службы, чтобы сделать его доступным для приложения.</span><span class="sxs-lookup"><span data-stu-id="00f80-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="00f80-151">Войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="00f80-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="00f80-152">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="00f80-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="00f80-153">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="00f80-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="00f80-154">После входа в меню слева щелкните **учетные записи хранения** .</span><span class="sxs-lookup"><span data-stu-id="00f80-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="00f80-156">Слово **New** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="00f80-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="00f80-157">На вкладке **учетные записи хранения** щелкните **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="00f80-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="00f80-159">На панели **Создание учетной записи хранения** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="00f80-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="00f80-160">Введите **имя** для своей учетной записи. Имейте в виду, что это поле принимает только цифры и строчные буквы.</span><span class="sxs-lookup"><span data-stu-id="00f80-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="00f80-161">В качестве **модели развертывания** выберите **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="00f80-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="00f80-162">В качестве **типа учетной записи**выберите **хранилище (общее назначение v1)** .</span><span class="sxs-lookup"><span data-stu-id="00f80-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="00f80-163">Для **повышения производительности**выберите **стандартный**.</span><span class="sxs-lookup"><span data-stu-id="00f80-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="00f80-164">Для **репликации** выберите **геоизбыточное хранилище (RA-GRS) с доступом для чтения**.</span><span class="sxs-lookup"><span data-stu-id="00f80-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="00f80-165">Оставьте **защищенное перемещение обязательным** , как **отключено**.</span><span class="sxs-lookup"><span data-stu-id="00f80-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="00f80-166">Выберите **подписку**.</span><span class="sxs-lookup"><span data-stu-id="00f80-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="00f80-167">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="00f80-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="00f80-168">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="00f80-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="00f80-169">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="00f80-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="00f80-170">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="00f80-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="00f80-171">Определите **Расположение** группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="00f80-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="00f80-172">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="00f80-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="00f80-173">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="00f80-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="00f80-174">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="00f80-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="00f80-176">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="00f80-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="00f80-177">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="00f80-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="00f80-179">Глава 2-Машинное обучение Azure Studio</span><span class="sxs-lookup"><span data-stu-id="00f80-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="00f80-180">Чтобы использовать *машинное обучение Azure*, необходимо настроить экземпляр службы машинное обучение, чтобы сделать ее доступной для приложения.</span><span class="sxs-lookup"><span data-stu-id="00f80-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="00f80-181">На портале Azure щелкните **создать** в левом верхнем углу и найдите **рабочую область машинное обучение Studio**и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="00f80-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Машинное обучение Azure Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="00f80-183">На новой странице будет представлено описание службы **рабочей области машинное обучение Studio** .</span><span class="sxs-lookup"><span data-stu-id="00f80-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="00f80-184">В нижнем левом углу этого запроса нажмите кнопку " **создать** ", чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="00f80-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="00f80-185">После нажатия кнопки **создать**появится панель, где необходимо указать некоторые сведения о новой **службе машинное обучение Studio**:</span><span class="sxs-lookup"><span data-stu-id="00f80-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="00f80-186">Вставьте имя нужной **рабочей области** для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="00f80-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="00f80-187">Выберите **подписку**.</span><span class="sxs-lookup"><span data-stu-id="00f80-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="00f80-188">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="00f80-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="00f80-189">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="00f80-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="00f80-190">Рекомендуется, чтобы все службы Azure, связанные с одним проектом (например, в этих лабораториях), были в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="00f80-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="00f80-191">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="00f80-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="00f80-192">Определите **Расположение** группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="00f80-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="00f80-193">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="00f80-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="00f80-194">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="00f80-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="00f80-195">Вы должны использовать ту же группу ресурсов, которая использовалась для создания хранилища Azure, в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="00f80-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="00f80-196">В разделе **учетная запись хранения** щелкните **использовать существующий**, а затем в раскрывающемся меню выберите **учетную запись хранения** , созданную в последней главе.</span><span class="sxs-lookup"><span data-stu-id="00f80-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="00f80-197">Выберите нужную **ценовую категорию рабочей области** в раскрывающемся меню.</span><span class="sxs-lookup"><span data-stu-id="00f80-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="00f80-198">В разделе " **план веб-службы** " щелкните **создать** **,** а затем вставьте в текстовое поле имя.</span><span class="sxs-lookup"><span data-stu-id="00f80-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="00f80-199">В разделе **ценовая категория плана веб-службы** Выберите ценовую категорию по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="00f80-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="00f80-200">Уровень тестирования разработки под названием **DEVTEST Standard** должен быть доступен бесплатно.</span><span class="sxs-lookup"><span data-stu-id="00f80-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="00f80-201">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="00f80-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="00f80-202">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="00f80-202">Click **Create**.</span></span>

        ![Машинное обучение Azure Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="00f80-204">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="00f80-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="00f80-205">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="00f80-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Машинное обучение Azure Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="00f80-207">Щелкните уведомление, чтобы просмотреть новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="00f80-207">Click on the notification to explore your new Service instance.</span></span>

    ![Машинное обучение Azure Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="00f80-209">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="00f80-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="00f80-210">На отображаемой странице в разделе **Дополнительные ссылки** щелкните **запустить машинное обучение Studio**, чтобы браузер нанаправлялся на портал **машинное обучение Studio** .</span><span class="sxs-lookup"><span data-stu-id="00f80-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Машинное обучение Azure Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="00f80-212">Чтобы войти в Машинное обучение Studio, используйте кнопку **Вход** , расположенную в правом верхнем углу или в центре.</span><span class="sxs-lookup"><span data-stu-id="00f80-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Машинное обучение Azure Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="00f80-214">Глава 3-Машинное обучение Studio: Настройка набора данных</span><span class="sxs-lookup"><span data-stu-id="00f80-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="00f80-215">Одним из способов работы алгоритмов Машинное обучение является анализ существующих данных и последующая попытка прогнозировать будущие результаты на основе существующего набора данных.</span><span class="sxs-lookup"><span data-stu-id="00f80-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="00f80-216">Как правило, это означает, что чем больше существующих данных, тем лучше алгоритм будет прогнозировать будущие результаты.</span><span class="sxs-lookup"><span data-stu-id="00f80-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="00f80-217">Для этого курса предоставляется пример таблицы с именем Продуктстаблексв, который [можно скачать здесь](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="00f80-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00f80-218">Указанный zip-файл содержит как **продуктстаблексв** , так и **пакет unitypackage**, которые понадобятся в [главе 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="00f80-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="00f80-219">Этот пакет также предоставляется в этой главе, но разделяются на CSV-файл.</span><span class="sxs-lookup"><span data-stu-id="00f80-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="00f80-220">Этот образец набора данных содержит запись наиболее популярных объектов в каждый час каждого дня года 2017.</span><span class="sxs-lookup"><span data-stu-id="00f80-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Машинное обучение Studio: Настройка набора данных](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="00f80-222">Например, в день 1 из 2017 в 13:00-14:30 (час 13) наиболее производительный элемент был Salt и перца.</span><span class="sxs-lookup"><span data-stu-id="00f80-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="00f80-223">Этот образец таблицы содержит 9998 записей.</span><span class="sxs-lookup"><span data-stu-id="00f80-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="00f80-224">Вернитесь на портал **машинное обучение Studio** и добавьте эту таблицу в качестве **набора данных** для вашего машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="00f80-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="00f80-225">Для этого нажмите кнопку **+ создать** в левом нижнем углу экрана.</span><span class="sxs-lookup"><span data-stu-id="00f80-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Машинное обучение Studio: Настройка набора данных](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="00f80-227">Раздел появится снизу, и в нем есть панель навигации слева.</span><span class="sxs-lookup"><span data-stu-id="00f80-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="00f80-228">Щелкните **набор данных**, а затем справа от параметра **локальный файл**.</span><span class="sxs-lookup"><span data-stu-id="00f80-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Машинное обучение Studio: Настройка набора данных](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="00f80-230">Отправьте новый **набор данных** , выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="00f80-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="00f80-231">Появится окно Отправка, где можно **Просмотреть** жесткий диск для нового набора данных.</span><span class="sxs-lookup"><span data-stu-id="00f80-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Машинное обучение Studio: Настройка набора данных](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="00f80-233">После выбора и обратно в окне Отправка снимите флажок не потикать.</span><span class="sxs-lookup"><span data-stu-id="00f80-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="00f80-234">В текстовом поле ниже введите **продуктстаблексв. csv** в качестве имени для набора данных (хотя он должен быть добавлен автоматически).</span><span class="sxs-lookup"><span data-stu-id="00f80-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="00f80-235">С помощью раскрывающегося меню **тип**выберите **универсальный CSV-файл с заголовком (CSV)** .</span><span class="sxs-lookup"><span data-stu-id="00f80-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="00f80-236">Нажмите кнопку с галочкой в правом нижнем углу окна отправки, и ваш **набор данных** будет отправлен.</span><span class="sxs-lookup"><span data-stu-id="00f80-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="00f80-237">Глава 4-Машинное обучение Studio: эксперимент</span><span class="sxs-lookup"><span data-stu-id="00f80-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="00f80-238">Перед созданием системы машинного обучения необходимо создать эксперимент, чтобы проверить свою теорию данных.</span><span class="sxs-lookup"><span data-stu-id="00f80-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="00f80-239">С результатами вы узнаете, требуются ли дополнительные данные или нет никакой корреляции между данными и возможным результатом.</span><span class="sxs-lookup"><span data-stu-id="00f80-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="00f80-240">Чтобы начать создание эксперимента, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="00f80-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="00f80-241">Щелкните еще раз на кнопке **+ создать** в левом нижнем углу страницы, а затем щелкните **эксперимент** > **пустой эксперимент**.</span><span class="sxs-lookup"><span data-stu-id="00f80-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="00f80-243">Откроется новая страница с пустым экспериментом:</span><span class="sxs-lookup"><span data-stu-id="00f80-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="00f80-244">На панели слева разверните **сохраненные наборы данных** > **Мои наборы** данных и перетащите **продуктстаблексв** на **холст эксперимента**.</span><span class="sxs-lookup"><span data-stu-id="00f80-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="00f80-246">На панели слева разверните узел **Преобразование данных** > **пример и разбиение**.</span><span class="sxs-lookup"><span data-stu-id="00f80-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="00f80-247">Затем перетащите элемент « **разбить данные** » на **холст эксперимента**.</span><span class="sxs-lookup"><span data-stu-id="00f80-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="00f80-248">Элемент «разбиение данных» разделяет набор данных на две части.</span><span class="sxs-lookup"><span data-stu-id="00f80-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="00f80-249">Одна часть, которая будет использоваться для обучения алгоритма машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="00f80-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="00f80-250">Вторая часть будет использоваться для вычисления точности создаваемого алгоритма.</span><span class="sxs-lookup"><span data-stu-id="00f80-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="00f80-252">На правой панели (если выбран элемент «разделение данных» на холсте) измените **долю строк в первом выходном наборе данных** на **0,7**.</span><span class="sxs-lookup"><span data-stu-id="00f80-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="00f80-253">При этом данные будут разделены на две части, первая часть будет составлять 70% данных, а вторая часть будет состоять из оставшихся 30%.</span><span class="sxs-lookup"><span data-stu-id="00f80-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="00f80-254">Чтобы обеспечить разбиение данных в случайном порядке, убедитесь, что флажок **случайная разбивка** остается установленным.</span><span class="sxs-lookup"><span data-stu-id="00f80-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="00f80-256">Перетащите соединение из базового элемента **продуктстаблексв** на холста в верхнюю часть элемента данных разбиения.</span><span class="sxs-lookup"><span data-stu-id="00f80-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="00f80-257">Это приведет к подключению элементов и отправке выходного набора данных **продуктстаблексв** (данных) в данные разбиения.</span><span class="sxs-lookup"><span data-stu-id="00f80-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="00f80-259">На панели **эксперименты** слева разверните узел **машинное обучение** > **обучения**.</span><span class="sxs-lookup"><span data-stu-id="00f80-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="00f80-260">Перетащите элемент **обучение модели** в холст эксперимента.</span><span class="sxs-lookup"><span data-stu-id="00f80-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="00f80-261">Холст должен выглядеть так же, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="00f80-261">Your canvas should look the same as the below.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="00f80-263">В ***левом нижнем*** углу элемента « **разбиение данных** » перетащите соединение в **верхнюю правую** часть элемента « **обучение модели** ».</span><span class="sxs-lookup"><span data-stu-id="00f80-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="00f80-264">В модели обучения для обучения алгоритму будет использоваться первый 70%, разделенный на набор данных.</span><span class="sxs-lookup"><span data-stu-id="00f80-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="00f80-266">Выберите элемент **обучение модели** на холсте и на панели **свойства** (в правой части окна браузера) нажмите кнопку **Выбор столбца для запуска** .</span><span class="sxs-lookup"><span data-stu-id="00f80-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="00f80-267">В текстовом поле введите **Product** и нажмите клавишу **Ввод**. *продукт* будет установлен в качестве столбца для обучения прогнозов.</span><span class="sxs-lookup"><span data-stu-id="00f80-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="00f80-268">После этого щелкните **такт** в правом нижнем углу, чтобы закрыть диалоговое окно выбора.</span><span class="sxs-lookup"><span data-stu-id="00f80-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="00f80-270">Вы собираетесь обучить алгоритм **логистической регрессии с многоклассией** для прогнозирования наиболее проданного **продукта** на основе часа дня и даты.</span><span class="sxs-lookup"><span data-stu-id="00f80-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="00f80-271">В этом документе нет сведений о различных алгоритмах, предоставляемых Машинное обучение Azure Studio, но вы можете узнать больше на [странице машинное обучение Algorithm Памятка по](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet) .</span><span class="sxs-lookup"><span data-stu-id="00f80-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="00f80-272">На панели "элементы эксперимента" слева разверните узел **Машинное обучение** > **инициализировать модель** > **классификация**и перетащите элемент **логистической регрессии** на холст эксперимента.</span><span class="sxs-lookup"><span data-stu-id="00f80-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="00f80-273">Соедините выходные данные от нижней части **логистической регрессии класса**с верхним левым входом элемента **обучение модели** .</span><span class="sxs-lookup"><span data-stu-id="00f80-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="00f80-275">В списке элементов эксперимента на панели слева разверните **Машинное обучение** > **оценки**и перетащите элемент **модель оценки** на холст.</span><span class="sxs-lookup"><span data-stu-id="00f80-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="00f80-276">Соедините выходные данные от нижней части **модели обучения**с верхним левым входом **модели оценки**.</span><span class="sxs-lookup"><span data-stu-id="00f80-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="00f80-277">Соедините правый нижний вывод из раздела " **разбить данные**" к верхнему правому входу элемента **модели оценки** .</span><span class="sxs-lookup"><span data-stu-id="00f80-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="00f80-279">В списке элементов **эксперимента** на панели слева разверните **машинное обучение** > **оценить**и перетащите элемент **Оценка модели** на холст.</span><span class="sxs-lookup"><span data-stu-id="00f80-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="00f80-280">Соедините выходные данные **модели оценки** с верхним левым входом **модели Evaluate**.</span><span class="sxs-lookup"><span data-stu-id="00f80-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="00f80-282">Вы создали первый Машинное обучение эксперимент.</span><span class="sxs-lookup"><span data-stu-id="00f80-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="00f80-283">Теперь можно сохранить и запустить эксперимент.</span><span class="sxs-lookup"><span data-stu-id="00f80-283">You can now save and run the experiment.</span></span> <span data-ttu-id="00f80-284">В меню в нижней части страницы нажмите кнопку **сохранить** , чтобы сохранить эксперимент, а затем нажмите кнопку **выполнить** , чтобы запустить эксперимент.</span><span class="sxs-lookup"><span data-stu-id="00f80-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="00f80-286">**Состояние** эксперимента можно увидеть в правом верхнем углу холста.</span><span class="sxs-lookup"><span data-stu-id="00f80-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="00f80-287">Подождите некоторое время, пока эксперимент завершится.</span><span class="sxs-lookup"><span data-stu-id="00f80-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="00f80-288">Если у вас есть большой набор данных (реальный мир), скорее всего, для выполнения эксперимента может потребоваться несколько часов.</span><span class="sxs-lookup"><span data-stu-id="00f80-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="00f80-290">Щелкните правой кнопкой мыши элемент **Оценка модели** на холсте и в контекстном меню наведите указатель мыши на **результаты оценки**, а затем выберите **визуализировать**.</span><span class="sxs-lookup"><span data-stu-id="00f80-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="00f80-292">Результаты оценки будут отображаться, отображая прогнозируемые результаты и фактические результаты.</span><span class="sxs-lookup"><span data-stu-id="00f80-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="00f80-293">В этом случае используется 30% исходного набора данных, который был разделен ранее для оценки модели.</span><span class="sxs-lookup"><span data-stu-id="00f80-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="00f80-294">Результаты могут быть небольшими, в идеале в каждой строке будет выделено выделенный элемент в столбцах.</span><span class="sxs-lookup"><span data-stu-id="00f80-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="00f80-296">Закройте **результаты**.</span><span class="sxs-lookup"><span data-stu-id="00f80-296">Close the **Results**.</span></span>

24. <span data-ttu-id="00f80-297">Чтобы использовать новую обученную модель Машинное обучение необходимо предоставить ее в качестве **веб-службы**.</span><span class="sxs-lookup"><span data-stu-id="00f80-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="00f80-298">Для этого щелкните элемент меню **Настройка веб-службы** в меню в нижней части страницы и щелкните **прогнозная веб-служба**.</span><span class="sxs-lookup"><span data-stu-id="00f80-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="00f80-300">Будет создана новая вкладка, а также Объединенная модель для создания новой веб-службы.</span><span class="sxs-lookup"><span data-stu-id="00f80-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="00f80-301">В меню в нижней части страницы щелкните **сохранить**, а затем — **выполнить**.</span><span class="sxs-lookup"><span data-stu-id="00f80-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="00f80-302">Вы увидите состояние Обновлено в правом верхнем углу холста эксперимента.</span><span class="sxs-lookup"><span data-stu-id="00f80-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="00f80-304">После завершения работы в нижней части страницы появится кнопка **развернуть веб-службу** .</span><span class="sxs-lookup"><span data-stu-id="00f80-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="00f80-305">Все готово для развертывания веб-службы.</span><span class="sxs-lookup"><span data-stu-id="00f80-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="00f80-306">Щелкните **развернуть веб-службу** (классическая) в меню в нижней части страницы.</span><span class="sxs-lookup"><span data-stu-id="00f80-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="00f80-308">В браузере может появиться запрос на разрешение всплывающего окна, которое следует **Разрешить**, хотя может потребоваться еще раз нажать кнопку **развернуть веб-службу** , если страница развертывание не отображается.</span><span class="sxs-lookup"><span data-stu-id="00f80-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="00f80-309">После создания эксперимента вы будете перенаправлены на страницу **панели мониторинга** , где будет отображаться **ключ API** .</span><span class="sxs-lookup"><span data-stu-id="00f80-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="00f80-310">Скопируйте его в блокноте. в этот момент он понадобится в коде очень быстро.</span><span class="sxs-lookup"><span data-stu-id="00f80-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="00f80-311">После того как вы заметили ключ API, нажмите кнопку **запрос/ответ** в разделе **Конечная точка по умолчанию** под ключом.</span><span class="sxs-lookup"><span data-stu-id="00f80-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="00f80-313">Если нажать кнопку Тест на этой странице, можно будет ввести входные данные и просмотреть результат.</span><span class="sxs-lookup"><span data-stu-id="00f80-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="00f80-314">Введите **день** и **час**.</span><span class="sxs-lookup"><span data-stu-id="00f80-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="00f80-315">Оставьте поле ввода **продукта** пустым.</span><span class="sxs-lookup"><span data-stu-id="00f80-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="00f80-316">Затем нажмите кнопку **Confirm (подтвердить** ).</span><span class="sxs-lookup"><span data-stu-id="00f80-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="00f80-317">В выходных данных в нижней части страницы будет показан код JSON, представляющий вероятность выбора каждого продукта.</span><span class="sxs-lookup"><span data-stu-id="00f80-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="00f80-318">Откроется новая веб-страница, в которой будут показаны инструкции и некоторые примеры структуры запроса, необходимой для Машинное обучение Studio.</span><span class="sxs-lookup"><span data-stu-id="00f80-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="00f80-319">Скопируйте **URI запроса** , показанный на этой странице, в Блокнот.</span><span class="sxs-lookup"><span data-stu-id="00f80-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="00f80-321">Теперь вы создали систему машинного обучения, которая предоставляет наиболее вероятный продукт для продажи на основе исторических данных о покупках, сопоставленных с временем дня и дня года.</span><span class="sxs-lookup"><span data-stu-id="00f80-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="00f80-322">Для вызова веб-службы вам потребуется URL-адрес конечной точки службы и ключ API для службы.</span><span class="sxs-lookup"><span data-stu-id="00f80-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="00f80-323">Откройте вкладку **Использование** , расположенную в верхнем меню.</span><span class="sxs-lookup"><span data-stu-id="00f80-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="00f80-324">На странице сведения о **потреблении** будут отображены сведения, необходимые для вызова веб-службы из кода.</span><span class="sxs-lookup"><span data-stu-id="00f80-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="00f80-325">Сделайте копию **первичного ключа** и URL-адреса **запроса и ответа** .</span><span class="sxs-lookup"><span data-stu-id="00f80-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="00f80-326">Они понадобятся в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="00f80-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="00f80-327">Глава 5. Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="00f80-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="00f80-328">Настройка и тестирование иммерсивного наушников смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="00f80-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="00f80-329">Для этого курса **не** потребуется использовать контроллеры движения.</span><span class="sxs-lookup"><span data-stu-id="00f80-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="00f80-330">Если вам нужна поддержка настройки иммерсивного головного телефона, щелкните [здесь](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="00f80-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="00f80-331">Откройте **Unity** и создайте новый проект Unity с именем **MR\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="00f80-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="00f80-332">Убедитесь, что для типа проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="00f80-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="00f80-333">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="00f80-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="00f80-334">Перейдите к разделу **изменение** **параметров** > , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="00f80-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="00f80-335">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="00f80-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="00f80-336">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="00f80-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="00f80-337">Затем перейдите в раздел **файл** > **параметры сборки** и переключите платформу на **универсальная платформа Windows**, нажав кнопку ***коммутатора платформы*** .</span><span class="sxs-lookup"><span data-stu-id="00f80-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="00f80-338">Также убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="00f80-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="00f80-339">**Целевое устройство** настроено для **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="00f80-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="00f80-340">Для Microsoft HoloLens задайте для параметра **целевое устройство** значение *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="00f80-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="00f80-341">Для **типа сборки** задано значение **D3D**.</span><span class="sxs-lookup"><span data-stu-id="00f80-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="00f80-342">**Пакет SDK** установлен в значение " **Последняя установка**".</span><span class="sxs-lookup"><span data-stu-id="00f80-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="00f80-343">**Установлена последняя установленная** **версия Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="00f80-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="00f80-344">**Сборка и запуск** настроены на **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="00f80-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="00f80-345">Не беспокойтесь о настройке **сцен** прямо сейчас, так как они будут предоставлены позже.</span><span class="sxs-lookup"><span data-stu-id="00f80-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="00f80-346">Остальные параметры должны остаться в данный момент по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="00f80-346">The remaining settings should be left as default for now.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="00f80-348">В окне **параметры сборки** нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится **инспектор** .</span><span class="sxs-lookup"><span data-stu-id="00f80-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="00f80-349">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="00f80-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="00f80-350">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="00f80-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="00f80-351">Должна быть **экспериментальная** **версия среды выполнения** **сценариев** (эквивалент .NET 4,6)</span><span class="sxs-lookup"><span data-stu-id="00f80-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="00f80-352">**Серверная часть сценариев** должна быть ***.NET***</span><span class="sxs-lookup"><span data-stu-id="00f80-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="00f80-353">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="00f80-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="00f80-355">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="00f80-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="00f80-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="00f80-356">**InternetClient**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="00f80-358">На панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="00f80-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="00f80-360">Назад в **параметрах сборки** проект *Unity C#*  больше не является серым. Установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="00f80-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="00f80-361">Закройте окно параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="00f80-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="00f80-362">Сохраните проект (**файл > сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="00f80-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="00f80-363">Глава 6. Импорт пакета Unity Млпродуктс</span><span class="sxs-lookup"><span data-stu-id="00f80-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="00f80-364">Для этого курса необходимо скачать пакет ресурса Unity под названием [**Azure-MR-307. пакет unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="00f80-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="00f80-365">Этот пакет завершается с помощью сцены и всех объектов в этой предварительно построенной, что позволяет сосредоточиться на работе.</span><span class="sxs-lookup"><span data-stu-id="00f80-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="00f80-366">Предоставляется скрипт **шелфкипер** , хотя содержит только открытые переменные для структуры настройки сцены.</span><span class="sxs-lookup"><span data-stu-id="00f80-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="00f80-367">Вам потребуется выполнить все остальные разделы.</span><span class="sxs-lookup"><span data-stu-id="00f80-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="00f80-368">Чтобы импортировать этот пакет, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="00f80-368">To import this package:</span></span>

1.  <span data-ttu-id="00f80-369">Теперь, когда панель мониторинга Unity находится перед вами, щелкните **ресурсы** в меню в верхней части экрана, а затем щелкните **Импорт пакета, настраиваемый пакет**.</span><span class="sxs-lookup"><span data-stu-id="00f80-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Импорт пакета Unity Млпродуктс](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="00f80-371">С помощью средства выбора файлов выберите пакет **Azure-MR-307. пакет unitypackage** и нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="00f80-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="00f80-372">Отобразится список компонентов для этого актива.</span><span class="sxs-lookup"><span data-stu-id="00f80-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="00f80-373">Подтвердите импорт, нажав кнопку **Импорт**.</span><span class="sxs-lookup"><span data-stu-id="00f80-373">Confirm the import by clicking **Import**.</span></span>

    ![Импорт пакета Unity Млпродуктс](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="00f80-375">После завершения импорта вы увидите, что на **панели проекта**Unity появились новые папки.</span><span class="sxs-lookup"><span data-stu-id="00f80-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="00f80-376">Это трехмерные модели и соответствующие материалы, которые являются частью предварительно подготовленной сцены, с которой вы будете работать.</span><span class="sxs-lookup"><span data-stu-id="00f80-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="00f80-377">В этом курсе будет написана большая часть кода.</span><span class="sxs-lookup"><span data-stu-id="00f80-377">You will write the majority of the code in this course.</span></span>

    ![Импорт пакета Unity Млпродуктс](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="00f80-379">В папке " **Панель проекта** " щелкните папку " **сцены** " и дважды щелкните сцену внутри (под названием **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="00f80-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="00f80-380">Будет открыта сцена (см. изображение ниже).</span><span class="sxs-lookup"><span data-stu-id="00f80-380">The scene will open (see image below).</span></span> <span data-ttu-id="00f80-381">Если красные ромбы отсутствуют, просто нажмите кнопку **приспособлений** в правом верхнем углу **игровой панели**.</span><span class="sxs-lookup"><span data-stu-id="00f80-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Импорт пакета Unity Млпродуктс](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="00f80-383">Глава 7. Проверка библиотек DLL в Unity</span><span class="sxs-lookup"><span data-stu-id="00f80-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="00f80-384">Чтобы использовать библиотеки JSON (используемые для сериализации и десериализации), в пакет, который вы выполнили, реализована библиотека DLL Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="00f80-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="00f80-385">Библиотека должна иметь правильную конфигурацию, хотя она стоит проверять (особенно при возникновении проблем с кодом не работает).</span><span class="sxs-lookup"><span data-stu-id="00f80-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="00f80-386">Для этого выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="00f80-386">To do so:</span></span>

-  <span data-ttu-id="00f80-387">Щелкните файл Newtonsoft в папке plugins и посмотрите на **Панель инспектора**.</span><span class="sxs-lookup"><span data-stu-id="00f80-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="00f80-388">Убедитесь, что **любая платформа** имеет тактовую шкалу.</span><span class="sxs-lookup"><span data-stu-id="00f80-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="00f80-389">Перейдите на **вкладку UWP** , а также убедитесь, что не **обрабатывать** тика.</span><span class="sxs-lookup"><span data-stu-id="00f80-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Импорт библиотек DLL в Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="00f80-391">Глава 8. Создание класса Шелфкипер</span><span class="sxs-lookup"><span data-stu-id="00f80-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="00f80-392">Класс **шелфкипер** размещает методы, управляющие пользовательским интерфейсом и продуктами, порожденными в сцене.</span><span class="sxs-lookup"><span data-stu-id="00f80-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="00f80-393">Как часть импортированного пакета, вам будет предоставлен этот класс, хотя он неполон.</span><span class="sxs-lookup"><span data-stu-id="00f80-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="00f80-394">Теперь пора выполнить этот класс:</span><span class="sxs-lookup"><span data-stu-id="00f80-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="00f80-395">Дважды щелкните сценарий **шелфкипер** в папке **Scripts** , чтобы открыть его в **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="00f80-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="00f80-396">Замените весь код, существующий в скрипте, следующим кодом, который устанавливает время и дату и имеет метод для отображения продукта.</span><span class="sxs-lookup"><span data-stu-id="00f80-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="00f80-397">Не забудьте сохранить изменения в **Visual Studio** перед возвратом в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="00f80-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="00f80-398">Вернувшись в редактор Unity, убедитесь, что класс **шелфкипер** выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="00f80-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Создание класса Шелфкипер](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="00f80-400">Если в скрипте отсутствуют целевые объекты ссылок (т. е. *Дата (сетка текста)* ), просто перетащите соответствующие объекты с **панели Иерархия**в целевые поля.</span><span class="sxs-lookup"><span data-stu-id="00f80-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="00f80-401">При необходимости см. описание ниже.</span><span class="sxs-lookup"><span data-stu-id="00f80-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="00f80-402">Откройте массив **порожденных точек** в скрипте компонента **шелфкипер** , щелкнув его левой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="00f80-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="00f80-403">Подраздел будет выглядеть под названием **size**, который указывает размер массива.</span><span class="sxs-lookup"><span data-stu-id="00f80-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="00f80-404">Введите **3** в текстовое поле рядом с элементом **Размер** и нажмите клавишу **Ввод**, после чего будут созданы три слота.</span><span class="sxs-lookup"><span data-stu-id="00f80-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="00f80-405">В **иерархии** разверните объект **времени показа** (щелкнув правой кнопкой мыши стрелку рядом с ним).</span><span class="sxs-lookup"><span data-stu-id="00f80-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="00f80-406">Затем щелкните ***основную камеру*** в **иерархии**, чтобы **инспектор** покажет сведения о ней.</span><span class="sxs-lookup"><span data-stu-id="00f80-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="00f80-407">Выберите **основную камеру** на **панели Иерархия**.</span><span class="sxs-lookup"><span data-stu-id="00f80-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="00f80-408">Перетащите объекты **даты** и **времени** из **панели Иерархия** в текстовые слоты **даты** и **времени** в **инспекторе** **основной камеры** в компоненте **шелфкипер** .</span><span class="sxs-lookup"><span data-stu-id="00f80-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="00f80-409">Перетащите **точки порождения** с **панели Иерархия** (под объектом *полка* ) на 3 ссылки на **три** **элемента** , как показано на рисунке.</span><span class="sxs-lookup"><span data-stu-id="00f80-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Создание класса Шелфкипер](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="00f80-411">Глава 9. Создание класса Продуктпредиктион</span><span class="sxs-lookup"><span data-stu-id="00f80-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="00f80-412">Следующий класс, который предстоит создать, — это класс **продуктпредиктион** .</span><span class="sxs-lookup"><span data-stu-id="00f80-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="00f80-413">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="00f80-413">This class is responsible for:</span></span>

-   <span data-ttu-id="00f80-414">Запрос к экземпляру **службы машинное обучение** , в котором указываются текущие дата и время.</span><span class="sxs-lookup"><span data-stu-id="00f80-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="00f80-415">Десериализация ответа JSON в пригодных для использования данных.</span><span class="sxs-lookup"><span data-stu-id="00f80-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="00f80-416">Анализ данных с получением трех рекомендуемых продуктов.</span><span class="sxs-lookup"><span data-stu-id="00f80-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="00f80-417">Вызов методов класса **шелфкипер** для вывода данных в сцене.</span><span class="sxs-lookup"><span data-stu-id="00f80-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="00f80-418">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="00f80-418">To create this class:</span></span>

1.  <span data-ttu-id="00f80-419">Перейдите в папку « **скрипты** » на **панели «проект»** .</span><span class="sxs-lookup"><span data-stu-id="00f80-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="00f80-420">Щелкните правой кнопкой мыши внутри папки, **Создайте**  **C# скрипт** > .</span><span class="sxs-lookup"><span data-stu-id="00f80-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="00f80-421">Вызовите скрипт **продуктпредиктион**.</span><span class="sxs-lookup"><span data-stu-id="00f80-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="00f80-422">Дважды щелкните новый скрипт **продуктпредиктион** , чтобы открыть его в **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="00f80-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="00f80-423">Если появится диалоговое окно " **обнаружено изменение файла** ", щелкните \***перезагрузить решение**.</span><span class="sxs-lookup"><span data-stu-id="00f80-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="00f80-424">Добавьте следующие пространства имен в начало класса Продуктпредиктион:</span><span class="sxs-lookup"><span data-stu-id="00f80-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="00f80-425">Внутри класса **продуктпредиктион** вставьте следующие два объекта, состоящие из нескольких вложенных классов.</span><span class="sxs-lookup"><span data-stu-id="00f80-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="00f80-426">Эти классы используются для сериализации и десериализации JSON для службы Машинное обучение.</span><span class="sxs-lookup"><span data-stu-id="00f80-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="00f80-427">Затем добавьте следующие переменные выше предыдущего кода (чтобы код, связанный с JSON, находящийся в нижней части скрипта, ниже всего другого кода, и из него):</span><span class="sxs-lookup"><span data-stu-id="00f80-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="00f80-428">Не забудьте вставить конечную точку " **первичный ключ** " и " **запрос-ответ**" с машинное обучение портала в переменные здесь.</span><span class="sxs-lookup"><span data-stu-id="00f80-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="00f80-429">На приведенных ниже изображениях показано, где можно было взять ключ и конечную точку из.</span><span class="sxs-lookup"><span data-stu-id="00f80-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Машинное обучение Studio: эксперимент](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="00f80-432">Вставьте этот код в метод **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="00f80-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="00f80-433">Метод **Start ()** вызывается при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="00f80-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="00f80-434">Ниже приведен метод, собирающий дату и время из окон и преобразующий их в формат, который Машинное обучение эксперимент может использовать для сравнения с данными, хранящимися в таблице.</span><span class="sxs-lookup"><span data-stu-id="00f80-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="00f80-435">Метод **Update ()** можно **Удалить** , так как этот класс не будет его использовать.</span><span class="sxs-lookup"><span data-stu-id="00f80-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="00f80-436">Добавьте следующий метод, который будет сообщать текущую дату и время к Машинное обучение конечной точке и получить ответ в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="00f80-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="00f80-437">Добавьте следующий метод, который отвечает за десериализацию ответа JSON и передачу результата десериализации в класс **шелфкипер** .</span><span class="sxs-lookup"><span data-stu-id="00f80-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="00f80-438">В результате будут содержаться названия трех элементов, прогнозируемых для продажи наибольшей актуальности в текущей дате и времени.</span><span class="sxs-lookup"><span data-stu-id="00f80-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="00f80-439">Вставьте приведенный ниже код в класс **продуктпредиктион** под предыдущим методом.</span><span class="sxs-lookup"><span data-stu-id="00f80-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="00f80-440">Сохраните **Visual Studio** и зашлем обратно в **Unity**.</span><span class="sxs-lookup"><span data-stu-id="00f80-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="00f80-441">Перетащите скрипт класса **продуктпредиктион** из папки **script** на **основной объект Camera** .</span><span class="sxs-lookup"><span data-stu-id="00f80-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="00f80-442">Сохраните сцену и **файл** проекта > **сохранить сцену или файл** > **сохранить проект**.</span><span class="sxs-lookup"><span data-stu-id="00f80-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="00f80-443">Глава 10. Создание решения UWP</span><span class="sxs-lookup"><span data-stu-id="00f80-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="00f80-444">Теперь пора создать проект как решение UWP, чтобы его можно было запускать как автономное приложение.</span><span class="sxs-lookup"><span data-stu-id="00f80-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="00f80-445">Для сборки:</span><span class="sxs-lookup"><span data-stu-id="00f80-445">To Build:</span></span>

1.  <span data-ttu-id="00f80-446">Сохраните текущую сцену, щелкнув **файл** > **сохранить сцены**.</span><span class="sxs-lookup"><span data-stu-id="00f80-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="00f80-447">Выберите **файл** > **параметры сборки**</span><span class="sxs-lookup"><span data-stu-id="00f80-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="00f80-448">Установите флажок **проекты Unity C#**  (это важно, так как он позволит изменять классы после завершения сборки).</span><span class="sxs-lookup"><span data-stu-id="00f80-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="00f80-449">Щелкните **Добавить открытые сцены**,</span><span class="sxs-lookup"><span data-stu-id="00f80-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="00f80-450">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="00f80-450">Click **Build**.</span></span>

    ![Создание решения UWP](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="00f80-452">Вам будет предложено выбрать папку, в которой нужно построить решение.</span><span class="sxs-lookup"><span data-stu-id="00f80-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="00f80-453">Создайте папку **Builds** и в этой папке создайте другую папку с соответствующим именем по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="00f80-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="00f80-454">Щелкните новую папку, а затем выберите **выбрать папку**, чтобы начать сборку в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="00f80-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Создание решения UWP](images/AzureLabs-Lab7-55.png)

    ![Создание решения UWP](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="00f80-457">После того как Unity завершит сборку (может занять некоторое время), он откроет окно **проводника** в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).</span><span class="sxs-lookup"><span data-stu-id="00f80-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="00f80-458">Глава 11. Развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="00f80-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="00f80-459">Чтобы развернуть приложение, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="00f80-459">To deploy your application:</span></span>

1.  <span data-ttu-id="00f80-460">Перейдите к новой сборке Unity (папка **приложения** ) и откройте файл решения в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="00f80-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="00f80-461">После открытия Visual Studio необходимо восстановить пакеты NuGet, которые можно выполнить, щелкнув правой кнопкой мыши решение MachineLearningLab_Build, из обозреватель решений (в правой части Visual Studio) и выбрав команду восстановить пакеты NuGet:</span><span class="sxs-lookup"><span data-stu-id="00f80-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Добавление пакетов NuGet](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="00f80-463">В конфигурации решения выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="00f80-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="00f80-464">На платформе решения выберите **x86**, **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="00f80-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="00f80-465">Для Microsoft HoloLens может быть проще установить этот параметр на *Удаленный компьютер*, чтобы вы не были подключены к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="00f80-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="00f80-466">Однако необходимо также выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="00f80-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="00f80-467">Определите **IP-адрес** HoloLens, который можно найти в *параметрах > сети & Интернет > Wi-Fi > Дополнительные параметры*. IPv4 — это адрес, который следует использовать.</span><span class="sxs-lookup"><span data-stu-id="00f80-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="00f80-468">Убедитесь, **что включен** **режим разработчика** ; находится в *параметрах > Update & > безопасности для разработчиков*.</span><span class="sxs-lookup"><span data-stu-id="00f80-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Добавление пакетов NuGet](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="00f80-470">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение на компьютер.</span><span class="sxs-lookup"><span data-stu-id="00f80-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="00f80-471">Теперь приложение должно отобразиться в списке установленных приложений, готовых к запуску.</span><span class="sxs-lookup"><span data-stu-id="00f80-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="00f80-472">При запуске приложения Mixed Reality вы увидите, что оно было настроено в сцене Unity, и из инициализации данные, настроенные в Azure, будут получены.</span><span class="sxs-lookup"><span data-stu-id="00f80-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="00f80-473">Данные будут десериализованы в приложении, а три лучших результата для текущей даты и времени будут предоставлены визуально, как три модели в Bench.</span><span class="sxs-lookup"><span data-stu-id="00f80-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="00f80-474">Законченное Машинное обучение приложение</span><span class="sxs-lookup"><span data-stu-id="00f80-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="00f80-475">Поздравляем, вы создали приложение смешанной реальности, которое использует Машинное обучение Azure, чтобы сделать прогнозы данных и отображать их на сцене.</span><span class="sxs-lookup"><span data-stu-id="00f80-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Добавление пакетов NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="00f80-477">Тренировок</span><span class="sxs-lookup"><span data-stu-id="00f80-477">Exercise</span></span>

<span data-ttu-id="00f80-478">**Упражнение 1**</span><span class="sxs-lookup"><span data-stu-id="00f80-478">**Exercise 1**</span></span>

<span data-ttu-id="00f80-479">Поэкспериментируйте с порядком сортировки приложения и покажите три нижние прогнозы на полке, так как эти данные потенциально также могут быть полезными.</span><span class="sxs-lookup"><span data-stu-id="00f80-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="00f80-480">**Упражнение 2**</span><span class="sxs-lookup"><span data-stu-id="00f80-480">**Exercise 2**</span></span>

<span data-ttu-id="00f80-481">Использование **таблиц Azure** заполняет новую таблицу сведениями о погоде и создает новый эксперимент с помощью данных.</span><span class="sxs-lookup"><span data-stu-id="00f80-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
