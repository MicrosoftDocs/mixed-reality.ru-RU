---
title: Г-н и Azure 307 - машинного обучения
description: Выполните этот курс, чтобы узнать, как реализовать приложение смешанной реальности студии машинного обучения Azure.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, руководства, api, машинное обучение, ml, студия машинного обучения, hololens, насыщенные, виртуальной реальности
ms.openlocfilehash: 93263817df0fd809a09b32c1b34a636eab7026a1
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516041"
---
>[!NOTE]
><span data-ttu-id="10435-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="10435-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="10435-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="10435-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="10435-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="10435-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="10435-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="10435-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="10435-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="10435-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="10435-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="10435-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="10435-110">Г-н и Azure 307: Машинное обучение</span><span class="sxs-lookup"><span data-stu-id="10435-110">MR and Azure 307: Machine learning</span></span>

![конечный продукт-запуск](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="10435-112">В рамках этого курса вы узнаете, как добавить возможности машинного обучения (ML) приложение смешанной реальности, с помощью студии машинного обучения Azure.</span><span class="sxs-lookup"><span data-stu-id="10435-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="10435-113">*Студия машинного обучения Azure* — это служба Майкрософт, которая предоставляет разработчикам множество алгоритмов машинного обучения, которые могут помочь с входных данных, выходных данных, подготовки и визуализации.</span><span class="sxs-lookup"><span data-stu-id="10435-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="10435-114">Из этих компонентов то существует возможность разработки эксперимента прогнозной аналитики, выполнить на ней итерацию и использовать ее для обучения модели.</span><span class="sxs-lookup"><span data-stu-id="10435-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="10435-115">После обучения, можно сделать модель operational в облаке Azure, таким образом, чтобы его можно затем оценки новых данных.</span><span class="sxs-lookup"><span data-stu-id="10435-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="10435-116">Дополнительные сведения см. в статье [странице студии машинного обучения Azure](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="10435-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="10435-117">Оформили этот курс, вы получите приложение иммерсивных гарнитуры смешанной реальности и будет узнали, как выполнить следующие:</span><span class="sxs-lookup"><span data-stu-id="10435-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="10435-118">Создать таблицу с данными продаж для *студии машинного обучения Azure* портала и проектирования алгоритм для прогнозирования будущих продаж популярных элементов.</span><span class="sxs-lookup"><span data-stu-id="10435-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="10435-119">Создание **проекта Unity**, который может получать и интерпретировать данные прогноза из службы машинного Обучения.</span><span class="sxs-lookup"><span data-stu-id="10435-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="10435-120">Отобразить данные прогнозирование визуально в **проекта Unity**, до предоставления самыми популярными материалами продаж на полке.</span><span class="sxs-lookup"><span data-stu-id="10435-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="10435-121">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="10435-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="10435-122">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="10435-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="10435-123">Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="10435-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="10435-124">Этот курс — это автономное руководство, которые не предусматривают любых других смешанной реальности лабораторий, напрямую.</span><span class="sxs-lookup"><span data-stu-id="10435-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="10435-125">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="10435-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="10435-126">Курс</span><span class="sxs-lookup"><span data-stu-id="10435-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="10435-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="10435-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="10435-128"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="10435-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="10435-129">Г-н и Azure 307: Машинное обучение</span><span class="sxs-lookup"><span data-stu-id="10435-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="10435-130">✔️</span><span class="sxs-lookup"><span data-stu-id="10435-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="10435-131">✔️</span><span class="sxs-lookup"><span data-stu-id="10435-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="10435-132">Хотя этот курс основное внимание уделяется Windows Mixed Reality иммерсивную (VR), можно также применить полученные знания в этом курсе для Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10435-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="10435-133">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="10435-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="10435-134">При использовании HoloLens, вы можете заметить некоторые echo во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="10435-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10435-135">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="10435-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="10435-136">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="10435-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="10435-137">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="10435-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="10435-138">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства статье](install-the-tools.md), хотя следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .</span><span class="sxs-lookup"><span data-stu-id="10435-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="10435-139">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="10435-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="10435-140">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="10435-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="10435-141">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="10435-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10435-142">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="10435-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10435-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="10435-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10435-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="10435-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="10435-145">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="10435-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="10435-146">Доступ к Интернету для настройки Azure и получения данных машинного Обучения</span><span class="sxs-lookup"><span data-stu-id="10435-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="10435-147">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="10435-147">Before you start</span></span>

<span data-ttu-id="10435-148">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="10435-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="10435-149">Глава 1 - установки учетная запись хранения Azure</span><span class="sxs-lookup"><span data-stu-id="10435-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="10435-150">Чтобы использовать Azure Translator API, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="10435-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="10435-151">Войдите в [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="10435-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="10435-152">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="10435-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="10435-153">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="10435-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="10435-154">После входа в систему щелкните **учетные записи хранения** в меню слева.</span><span class="sxs-lookup"><span data-stu-id="10435-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="10435-156">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="10435-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="10435-157">На **учетные записи хранения** , щелкните на **добавить**.</span><span class="sxs-lookup"><span data-stu-id="10435-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="10435-159">В **создать учетную запись хранения** панели:</span><span class="sxs-lookup"><span data-stu-id="10435-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="10435-160">Вставить **имя** для вашей учетной записи, помните, это поле принимает только цифры и строчные буквы.</span><span class="sxs-lookup"><span data-stu-id="10435-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="10435-161">Для **модели развертывания,** выберите **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="10435-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="10435-162">Для **тип учетной записи**выберите **хранилища (общего назначения версии 1)** .</span><span class="sxs-lookup"><span data-stu-id="10435-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="10435-163">Для **производительности**выберите **стандартный**.</span><span class="sxs-lookup"><span data-stu-id="10435-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="10435-164">Для **репликации** выберите **Read-access геоизбыточного хранилища (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="10435-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="10435-165">Оставьте **требуется безопасное перемещение** как **отключено**.</span><span class="sxs-lookup"><span data-stu-id="10435-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="10435-166">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="10435-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="10435-167">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="10435-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="10435-168">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="10435-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="10435-169">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="10435-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="10435-170">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="10435-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="10435-171">Определить **расположение** для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="10435-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="10435-172">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="10435-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="10435-173">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="10435-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="10435-174">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="10435-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="10435-176">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="10435-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="10435-177">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="10435-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="10435-179">Глава 2 - студии машинного обучения Azure</span><span class="sxs-lookup"><span data-stu-id="10435-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="10435-180">Чтобы использовать *машинного обучения Azure*, необходимо настроить экземпляр службы машинного обучения, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="10435-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="10435-181">На портале Azure щелкните **New** в левом верхнем углу, а поиск **рабочая область студии машинного обучения**, нажмите клавишу **ввод**.</span><span class="sxs-lookup"><span data-stu-id="10435-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="10435-183">Новая страница будет предоставить описание **рабочая область студии машинного обучения** службы.</span><span class="sxs-lookup"><span data-stu-id="10435-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="10435-184">В нижней левой части этого запроса, нажмите кнопку **создать** кнопку, чтобы создать ассоциацию с этой службой.</span><span class="sxs-lookup"><span data-stu-id="10435-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="10435-185">Когда вы перейдете на **создать**, будет отображаться панель, где необходимо предоставить некоторые сведения о новой **службы студии машинного обучения**:</span><span class="sxs-lookup"><span data-stu-id="10435-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="10435-186">Вставить нужный **имя рабочей области** для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="10435-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="10435-187">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="10435-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="10435-188">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="10435-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="10435-189">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="10435-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="10435-190">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="10435-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="10435-191">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="10435-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="10435-192">Определить **расположение** для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="10435-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="10435-193">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="10435-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="10435-194">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="10435-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="10435-195">Следует использовать ту же группу ресурсов, которую вы использовали для создания хранилища Azure в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="10435-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="10435-196">Для **учетной записи хранения** щелкните **использовать существующий**, затем щелкните раскрывающееся меню и щелкните **учетной записи хранения** созданный в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="10435-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="10435-197">Выберите соответствующий **ценовой категории рабочей области** автоматически, в раскрывающемся меню.</span><span class="sxs-lookup"><span data-stu-id="10435-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="10435-198">В рамках **план веб-службы** щелкните **создать** **новых,** в текстовом поле введите ее имя.</span><span class="sxs-lookup"><span data-stu-id="10435-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="10435-199">Из **ценовой план веб-службы** выберите Ценовая категория по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="10435-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="10435-200">Разработки и тестирования уровень **DEVTEST стандартный** должны быть доступны вам бесплатно.</span><span class="sxs-lookup"><span data-stu-id="10435-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="10435-201">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="10435-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="10435-202">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="10435-202">Click **Create**.</span></span>

        ![Студия машинного обучения Azure](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="10435-204">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="10435-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="10435-205">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="10435-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="10435-207">Щелкните уведомление, чтобы изучить ваш новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="10435-207">Click on the notification to explore your new Service instance.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="10435-209">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="10435-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="10435-210">На странице отображается, в разделе **Дополнительные ссылки** щелкните **запуска студии машинного обучения**, который будет направлять в браузере **студии машинного обучения** портал.</span><span class="sxs-lookup"><span data-stu-id="10435-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="10435-212">Используйте **Sign In** кнопки в правом верхнем углу или в центре, чтобы войти в студию машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="10435-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="10435-214">Глава 3 - студии машинного обучения: Настройка набора данных</span><span class="sxs-lookup"><span data-stu-id="10435-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="10435-215">Одним из способов работы алгоритмов машинного обучения по анализа существующих данных, а затем попытаться спрогнозировать будущие результаты на основе существующего набора данных.</span><span class="sxs-lookup"><span data-stu-id="10435-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="10435-216">Это обычно означает, что у вас есть, тем лучше алгоритм будет в прогнозировании будущих результатов более существующих данных.</span><span class="sxs-lookup"><span data-stu-id="10435-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="10435-217">Образец таблицы вам предоставляется, этот курс вызывается [ProductsTableCSV и может быть скачан здесь](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="10435-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10435-218">Выше ZIP-файл содержит оба **ProductsTableCSV** и **.unitypackage**, которые потребуются в [Глава 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="10435-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="10435-219">Этот пакет также предоставляется в рамках соответствующей главы, хотя отдельные CSV-файл.</span><span class="sxs-lookup"><span data-stu-id="10435-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="10435-220">Этот пример набора данных содержит запись популярных объектов на каждый час каждый день 2017 года.</span><span class="sxs-lookup"><span data-stu-id="10435-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Студия машинного обучения: Настройка набора данных](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="10435-222">Например, на 1 день 2017 г., в 13: 00 (час 13), центр ознакомительного программного обеспечения элемент был соль и Перец.</span><span class="sxs-lookup"><span data-stu-id="10435-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="10435-223">Этот пример таблицы содержит 9998 записи.</span><span class="sxs-lookup"><span data-stu-id="10435-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="10435-224">Вернитесь к **студии машинного обучения** портала, и добавить эту таблицу как **набора данных** для вашей машинного Обучения.</span><span class="sxs-lookup"><span data-stu-id="10435-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="10435-225">Это можно сделать, щелкнув **+ создать** кнопку в левом нижнем углу экрана.</span><span class="sxs-lookup"><span data-stu-id="10435-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Студия машинного обучения: Настройка набора данных](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="10435-227">Раздел будет снизу и в наличии панели навигации слева.</span><span class="sxs-lookup"><span data-stu-id="10435-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="10435-228">Нажмите кнопку **набора данных**, а затем в правой части, **из локального файла**.</span><span class="sxs-lookup"><span data-stu-id="10435-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Студия машинного обучения: Настройка набора данных](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="10435-230">Передать новый **набора данных** , сделав следующее:</span><span class="sxs-lookup"><span data-stu-id="10435-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="10435-231">Будет открыто окно отправки, где вы можете **Обзор** жестком диске для нового набора данных.</span><span class="sxs-lookup"><span data-stu-id="10435-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Студия машинного обучения: Настройка набора данных](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="10435-233">После выбора и обратно в окне передачи, оставьте флажок снятом.</span><span class="sxs-lookup"><span data-stu-id="10435-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="10435-234">В текстовом поле ниже, введите **ProductsTableCSV.csv** как имя для набора данных (хотя автоматически добавляются).</span><span class="sxs-lookup"><span data-stu-id="10435-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="10435-235">С помощью раскрывающееся меню для **тип**выберите **универсальный CSV-файл с заголовком (CSV)** .</span><span class="sxs-lookup"><span data-stu-id="10435-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="10435-236">Нажмите клавишу деления в правом нижнем углу окна передачи и **набора данных** будут отправлены.</span><span class="sxs-lookup"><span data-stu-id="10435-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="10435-237">Глава 4 – студии машинного обучения: Эксперимент</span><span class="sxs-lookup"><span data-stu-id="10435-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="10435-238">Перед созданием машинного обучения системы, необходимо будет эксперимент, проверяемый на теории о своих данных.</span><span class="sxs-lookup"><span data-stu-id="10435-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="10435-239">С результатами вы будете знать, если вам нужно больше данных, или в том случае, если нет никакой корреляции между данными и возможный результат.</span><span class="sxs-lookup"><span data-stu-id="10435-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="10435-240">Чтобы приступить к созданию эксперимента:</span><span class="sxs-lookup"><span data-stu-id="10435-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="10435-241">Снова щелкните **+ создать** кнопку в левом нижнем углу страницы, а затем **эксперимента** > **пустой эксперимент**.</span><span class="sxs-lookup"><span data-stu-id="10435-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="10435-243">Новая страница будет отображаться с пустой эксперимент:</span><span class="sxs-lookup"><span data-stu-id="10435-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="10435-244">На панели слева разверните **сохраненные наборы данных* > *Мои наборы данных** и перетащите **ProductsTableCSV** в **Холст эксперимента**.</span><span class="sxs-lookup"><span data-stu-id="10435-244">From the panel on the left expand **Saved Datasets* > *My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="10435-246">На панели слева разверните **преобразования данных** > **выборка и разбиение**.</span><span class="sxs-lookup"><span data-stu-id="10435-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="10435-247">Затем перетащите **разбиение данных** элемент в **эксперимента**.</span><span class="sxs-lookup"><span data-stu-id="10435-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="10435-248">Элемент разделения данных будет разделить набор данных на две части.</span><span class="sxs-lookup"><span data-stu-id="10435-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="10435-249">Одной из частей будет использоваться для обучения алгоритма машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="10435-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="10435-250">Вторая часть будет использоваться для оценки точности алгоритма создан.</span><span class="sxs-lookup"><span data-stu-id="10435-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="10435-252">На панели справа (во время разбиения данных выбран элемент на холсте) изменить **доля строк в первый выходной набор данных** для **0,7**.</span><span class="sxs-lookup"><span data-stu-id="10435-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="10435-253">Это будет разбить данные на две части, первая часть будет 70% данных, а вторая часть будет оставшиеся 30%.</span><span class="sxs-lookup"><span data-stu-id="10435-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="10435-254">Чтобы убедиться, что данные разбиваются случайным образом, убедитесь, что **случайного разбиения** снимайте флажок.</span><span class="sxs-lookup"><span data-stu-id="10435-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="10435-256">Перетащите подключение из основание системы счисления **ProductsTableCSV** элемента на холсте вверху элемента разделения данных.</span><span class="sxs-lookup"><span data-stu-id="10435-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="10435-257">Это будет подключить элементы и отправлять **ProductsTableCSV** выходные данные набора данных (данные) для разделения входных данных.</span><span class="sxs-lookup"><span data-stu-id="10435-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="10435-259">В **экспериментов** на левой панели, разверните узел \**машинного обучения* > \* Train \*\*.</span><span class="sxs-lookup"><span data-stu-id="10435-259">In the **Experiments** panel on the left side, expand \**Machine Learning* > \*Train\*\*.</span></span> <span data-ttu-id="10435-260">Перетащите **Обучение модели** элемент out на холст эксперимента.</span><span class="sxs-lookup"><span data-stu-id="10435-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="10435-261">Холст должен выглядеть так же, как ниже.</span><span class="sxs-lookup"><span data-stu-id="10435-261">Your canvas should look the same as the below.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="10435-263">Из ***нижнем левом углу*** из **разбиение данных** элементов перетащите соединение **вверху справа** из **Обучение модели** элемента.</span><span class="sxs-lookup"><span data-stu-id="10435-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="10435-264">Первого разбиения 70% из набора данных будет использоваться Обучение модели для обучения алгоритму.</span><span class="sxs-lookup"><span data-stu-id="10435-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="10435-266">Выберите **Обучение модели** элемент на холсте, а также на **свойства** панели (в правой части окна браузера) выберите **запустить средство выбора столбцов** кнопки.</span><span class="sxs-lookup"><span data-stu-id="10435-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="10435-267">В текстовом поле введите **продукта** и нажмите клавишу **ввод**, *продукта* будет установлен в качестве столбца для обучения прогнозов.</span><span class="sxs-lookup"><span data-stu-id="10435-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="10435-268">После этого щелкните **делений** в нижнем правом углу, чтобы закрыть диалоговое окно выбора.</span><span class="sxs-lookup"><span data-stu-id="10435-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="10435-270">Вы собираетесь обучения **Мультиклассовая логистическая Регрессия** алгоритм для прогнозирования наиболее популярное **продукта** зависимости от часа дня и даты.</span><span class="sxs-lookup"><span data-stu-id="10435-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="10435-271">Это выходит за рамки этого документа, чтобы подробно описывается различных алгоритмов, предоставляемых студией машинного обучения Azure, однако вы подробнее можно узнать из [машины обучения Памятка по алгоритмам](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="10435-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="10435-272">Из панели элементов эксперимента в левой части разверните \*\**машинного обучения* > *Initialize Model* > \* классификации \*\*\* и перетащите **Мультиклассовой логистической регрессии**  элементов на холст эксперимента.</span><span class="sxs-lookup"><span data-stu-id="10435-272">From the experiment items panel on the left, expand \*\**Machine Learning* > *Initialize Model* > \*Classification\*\*\*, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="10435-273">Соедините выход, в нижней части **Мультиклассовая логистическая Регрессия**, на верхний левый вход **Обучение модели** элемента.</span><span class="sxs-lookup"><span data-stu-id="10435-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="10435-275">В списке элементов эксперимента на панели слева разверните узел \**машинного обучения* > \* оценка \*\* и перетащите **Score Model** элементов на холст.</span><span class="sxs-lookup"><span data-stu-id="10435-275">In list of experiment items in the panel on the left, expand \**Machine Learning* > \*Score\*\*, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="10435-276">Соедините выход, в нижней части **Обучение модели**, на верхний левый вход **оценка модели**.</span><span class="sxs-lookup"><span data-stu-id="10435-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="10435-277">Соедините выход из нижнего правого **разбиение данных**, на верхний правый вход  **Score Model* элемент*.</span><span class="sxs-lookup"><span data-stu-id="10435-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model* item*.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="10435-279">В списке **эксперимента** элементы на панели слева разверните \*\**машинного обучения* > \* Evaluate \*\*\* и перетащите **Evaluate Model** элементов на холст.</span><span class="sxs-lookup"><span data-stu-id="10435-279">In the list of **Experiment** items in the panel on the left, expand \*\**Machine Learning* > \*Evaluate\*\*\*, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="10435-280">Соедините выход из **Score Model** на верхний левый вход **Evaluate Model**.</span><span class="sxs-lookup"><span data-stu-id="10435-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="10435-282">Вы создали свой первый эксперимент обучения машины.</span><span class="sxs-lookup"><span data-stu-id="10435-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="10435-283">Теперь можно сохранить и запустить эксперимент.</span><span class="sxs-lookup"><span data-stu-id="10435-283">You can now save and run the experiment.</span></span> <span data-ttu-id="10435-284">В меню в нижней части страницы щелкните **Сохранить** кнопку, чтобы сохранить свой эксперимент и нажмите кнопку **запуска** запуск эксперимента.</span><span class="sxs-lookup"><span data-stu-id="10435-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="10435-286">Вы увидите **состояние** в верхней правой части холста эксперимента.</span><span class="sxs-lookup"><span data-stu-id="10435-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="10435-287">Подождите несколько секунд для эксперимента завершить.</span><span class="sxs-lookup"><span data-stu-id="10435-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="10435-288">Если у вас есть набор данных больших (реальном мире) вполне вероятно, что эксперимента может занять часов для выполнения.</span><span class="sxs-lookup"><span data-stu-id="10435-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="10435-290">Щелкните правой кнопкой мыши **Evaluate Model** элемент на холсте и из контекстного меню при наведении указателя мыши мыши над **результаты оценки**, а затем выберите **визуализировать**.</span><span class="sxs-lookup"><span data-stu-id="10435-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="10435-292">Результаты оценки отображаются отображение прогнозируемых выходных данных и фактические результаты.</span><span class="sxs-lookup"><span data-stu-id="10435-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="10435-293">При этом используется 30% исходного набора данных, который был ранее, разделение для оценки модели.</span><span class="sxs-lookup"><span data-stu-id="10435-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="10435-294">Вы увидите, что результаты не отлично, в идеале вам будет иметь наибольший номер в каждой строке размещения выделенный элемент в столбцах.</span><span class="sxs-lookup"><span data-stu-id="10435-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="10435-296">Закрыть **результаты**.</span><span class="sxs-lookup"><span data-stu-id="10435-296">Close the **Results**.</span></span>

24. <span data-ttu-id="10435-297">В использовании обученной модели машинного обучения, необходимо предоставлять его как **веб-службы**.</span><span class="sxs-lookup"><span data-stu-id="10435-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="10435-298">Чтобы сделать это, щелкните **настроить веб-службу** меню в меню в нижней части страницы и щелкните на **прогнозной веб-службы**.</span><span class="sxs-lookup"><span data-stu-id="10435-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="10435-300">Будет создана новая вкладка, и обучение модели объединяются для создания новой веб-службы.</span><span class="sxs-lookup"><span data-stu-id="10435-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="10435-301">В меню в нижней части страницы щелкните **Сохранить**, затем нажмите кнопку **запуска**.</span><span class="sxs-lookup"><span data-stu-id="10435-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="10435-302">Вы увидите состояние обновления в правом верхнем углу холста эксперимента.</span><span class="sxs-lookup"><span data-stu-id="10435-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="10435-304">После завершения работы, **Deploy Web Service** кнопка будет отображаться в нижней части страницы.</span><span class="sxs-lookup"><span data-stu-id="10435-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="10435-305">Вы готовы к развертыванию веб-службы.</span><span class="sxs-lookup"><span data-stu-id="10435-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="10435-306">Нажмите кнопку **Deploy Web Service** (классической) в меню в нижней части страницы.</span><span class="sxs-lookup"><span data-stu-id="10435-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="10435-308">Ваш браузер может запросить чтобы разрешить всплывающее окно, в которой следует **Разрешить**, хотя может потребоваться нажать **Deploy Web Service** опять же, если на странице развертывание не отображается.</span><span class="sxs-lookup"><span data-stu-id="10435-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="10435-309">После создания эксперимента вы будете перенаправлены к **панели мониторинга** страницы, где у вас будет вашей **ключ API** отображается.</span><span class="sxs-lookup"><span data-stu-id="10435-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="10435-310">Скопируйте его в Блокнот в данный момент, он потребуется в коде очень скоро.</span><span class="sxs-lookup"><span data-stu-id="10435-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="10435-311">Когда вы заметили ключ API, нажмите кнопку **запрос/ОТВЕТ** кнопку в **конечная точка по умолчанию** разделе под ключ.</span><span class="sxs-lookup"><span data-stu-id="10435-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="10435-313">Если щелкнуть теста на этой странице можно ввести входные данные и просмотреть выходные данные.</span><span class="sxs-lookup"><span data-stu-id="10435-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="10435-314">Введите **день** и **час**.</span><span class="sxs-lookup"><span data-stu-id="10435-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="10435-315">Оставьте **продукта** запись пустым.</span><span class="sxs-lookup"><span data-stu-id="10435-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="10435-316">Нажмите кнопку **Подтверждение** кнопки.</span><span class="sxs-lookup"><span data-stu-id="10435-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="10435-317">JSON, представляющее вероятность каждого продукта, что выбор будут показаны результаты в нижней части страницы.</span><span class="sxs-lookup"><span data-stu-id="10435-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="10435-318">Новый веб-страницы откроется, отображение инструкции и примеры о структуре запроса, требующегося студии машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="10435-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="10435-319">Копировать **URI запроса** отображаются на этой странице в вашей Блокнот.</span><span class="sxs-lookup"><span data-stu-id="10435-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="10435-321">Теперь вы создали это система, обеспечивающие, скорее всего, для продажи продукта на основе исторических приобретения данных, соотносятся с временем дня года и машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="10435-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="10435-322">Чтобы вызвать веб-службы, вам потребуется URL-адрес конечной точки службы и ключ API для службы.</span><span class="sxs-lookup"><span data-stu-id="10435-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="10435-323">Щелкните **Consume** вкладки в верхней строке меню.</span><span class="sxs-lookup"><span data-stu-id="10435-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="10435-324">**Потребления** сведения будут отображаться сведения, необходимо будет вызывать веб-службы из кода.</span><span class="sxs-lookup"><span data-stu-id="10435-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="10435-325">Сделайте копию **первичный ключ** и **запрос-ответ** URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="10435-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="10435-326">Они потребуются в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="10435-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="10435-327">Глава 5 - Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="10435-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="10435-328">Настройка и проверка вашего смешанной реальности гарнитура Иммерсивных.</span><span class="sxs-lookup"><span data-stu-id="10435-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="10435-329">Вы будете **не** требуются контроллеры движения курс с демороликами.</span><span class="sxs-lookup"><span data-stu-id="10435-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="10435-330">Если вам нужна поддерживает настройку Иммерсивных гарнитура, нажмите кнопку [здесь](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="10435-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="10435-331">Откройте **Unity** и создайте новый проект Unity с именем **MR\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="10435-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="10435-332">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="10435-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="10435-333">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10435-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="10435-334">Перейдите к ***изменить* > *предпочтения*** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="10435-334">Go to ***Edit* > *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="10435-335">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="10435-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="10435-336">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="10435-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="10435-337">Перейдите к ***файл* > *параметры построения*** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув ***переключить платформу*** кнопки.</span><span class="sxs-lookup"><span data-stu-id="10435-337">Next, go to ***File* > *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="10435-338">Также убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="10435-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="10435-339">**Целевое устройство** присваивается **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="10435-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="10435-340">Microsoft HoloLens, задайте **целевое устройство** для *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="10435-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="10435-341">**Тип сборки** присваивается **D3D**.</span><span class="sxs-lookup"><span data-stu-id="10435-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="10435-342">**Пакет SDK для** присваивается **самую новую установленную**.</span><span class="sxs-lookup"><span data-stu-id="10435-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="10435-343">**Версия Visual Studio** присваивается **самую новую установленную**.</span><span class="sxs-lookup"><span data-stu-id="10435-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="10435-344">**Сборка и запуск** присваивается **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="10435-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="10435-345">Не беспокоиться о настройке **сцены** прямо сейчас, как они предоставляются в более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="10435-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="10435-346">Остальные параметры следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="10435-346">The remaining settings should be left as default for now.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="10435-348">В **параметры построения** щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где **инспектор** находится.</span><span class="sxs-lookup"><span data-stu-id="10435-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="10435-349">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="10435-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="10435-350">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="10435-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="10435-351">**Сценарии** **версии среды выполнения** должно быть **экспериментальные** (.NET 4.6 эквивалент)</span><span class="sxs-lookup"><span data-stu-id="10435-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="10435-352">**Создание сценариев серверной части** должно быть ***.NET***</span><span class="sxs-lookup"><span data-stu-id="10435-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="10435-353">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="10435-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="10435-355">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="10435-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="10435-356">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="10435-356">**InternetClient**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="10435-358">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется</span><span class="sxs-lookup"><span data-stu-id="10435-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="10435-360">Вернитесь в **параметры построения** *Unity C#*  проектов больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="10435-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="10435-361">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="10435-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="10435-362">Сохраните проект (**ФАЙЛ > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="10435-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="10435-363">Глава 6 - Импорт пакета MLProducts Unity</span><span class="sxs-lookup"><span data-stu-id="10435-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="10435-364">Для этого курса необходимо скачать пакет средств Unity [ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="10435-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="10435-365">Этот пакет поставляется со сцены, и объекты, предварительно созданные, вы сможете сосредоточиться на начало его все работает.</span><span class="sxs-lookup"><span data-stu-id="10435-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="10435-366">**ShelfKeeper** предоставляется скрипт, но содержит только открытые переменные, для установки структуры сцены.</span><span class="sxs-lookup"><span data-stu-id="10435-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="10435-367">Необходимо будет сделать все остальные разделы.</span><span class="sxs-lookup"><span data-stu-id="10435-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="10435-368">Для импорта этого пакета:</span><span class="sxs-lookup"><span data-stu-id="10435-368">To import this package:</span></span>

1.  <span data-ttu-id="10435-369">С помощью панели мониторинга Unity перед глазами, щелкните **активы** в меню в верхней части экрана, нажмите кнопку **Импорт пакета, пользовательского пакета**.</span><span class="sxs-lookup"><span data-stu-id="10435-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Импорт пакета MLProducts Unity](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="10435-371">Используйте средство выбора файлов для выбора **Azure-MR-307.unitypackage** пакета и нажмите кнопку **откройте**.</span><span class="sxs-lookup"><span data-stu-id="10435-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="10435-372">Список компонентов для этого ресурса будет отображаться пользователю.</span><span class="sxs-lookup"><span data-stu-id="10435-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="10435-373">Подтверждение импорта, щелкнув **импорта**.</span><span class="sxs-lookup"><span data-stu-id="10435-373">Confirm the import by clicking **Import**.</span></span>

    ![Импорт пакета MLProducts Unity](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="10435-375">После его завершения импорта можно заметить, что некоторые новые папки публиковались в игру на Unity **панель проекта**.</span><span class="sxs-lookup"><span data-stu-id="10435-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="10435-376">Это трехмерные модели и соответствующих материалов, которые являются частью готовых сцены, вы будете работать.</span><span class="sxs-lookup"><span data-stu-id="10435-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="10435-377">В этом курсе вы напишете большая часть кода.</span><span class="sxs-lookup"><span data-stu-id="10435-377">You will write the majority of the code in this course.</span></span>

    ![Импорт пакета MLProducts Unity](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="10435-379">В рамках **панель проекта** папке, щелкните на **сцены** папку и дважды щелкните внутри сцены (вызывается **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="10435-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="10435-380">Сцены откроется (см. рисунок ниже).</span><span class="sxs-lookup"><span data-stu-id="10435-380">The scene will open (see image below).</span></span> <span data-ttu-id="10435-381">Если отсутствуют red бубны, просто щелкните **элементы** кнопку в верхней правой части **панели Game**.</span><span class="sxs-lookup"><span data-stu-id="10435-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Импорт пакета MLProducts Unity](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="10435-383">Глава 7 - Проверка библиотек DLL в Unity</span><span class="sxs-lookup"><span data-stu-id="10435-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="10435-384">Чтобы использовать библиотеки JSON (используется для сериализации и десериализации), с пакетом, который отображался в реализована Newtonsoft DLL.</span><span class="sxs-lookup"><span data-stu-id="10435-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="10435-385">Библиотека должна иметь правильные настройки, хотя следует (особенно если у вас возникают проблемы с кодом не работает).</span><span class="sxs-lookup"><span data-stu-id="10435-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="10435-386">Для этого сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="10435-386">To do so:</span></span>

-  <span data-ttu-id="10435-387">Щелкните левой кнопкой мыши на файле Newtonsoft внутри папки подключаемых модулей и просмотрите **панели Инспектора**.</span><span class="sxs-lookup"><span data-stu-id="10435-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="10435-388">Убедитесь, что **Any платформы** установлен.</span><span class="sxs-lookup"><span data-stu-id="10435-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="10435-389">Перейдите к **вкладке UWP** и также обеспечивают **не обрабатывать** установлен.</span><span class="sxs-lookup"><span data-stu-id="10435-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Импорт библиотек DLL в Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="10435-391">Глава 8 - создать класс ShelfKeeper</span><span class="sxs-lookup"><span data-stu-id="10435-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="10435-392">**ShelfKeeper** класс размещает методы, определяющие пользовательского интерфейса и продуктов, порожденных в сцене.</span><span class="sxs-lookup"><span data-stu-id="10435-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="10435-393">В рамках импортированного пакета будет у пользователя имеется этот класс на то, что он не полон.</span><span class="sxs-lookup"><span data-stu-id="10435-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="10435-394">Теперь пришло время для завершения этого класса:</span><span class="sxs-lookup"><span data-stu-id="10435-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="10435-395">Дважды щелкните **ShelfKeeper** сценарий, в **сценарии** , откройте папку с **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="10435-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="10435-396">Замените весь код, существующий в скрипте следующим кодом, которое задает дату и время и имеет метод для отображения продукта.</span><span class="sxs-lookup"><span data-stu-id="10435-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

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

3.  <span data-ttu-id="10435-397">Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="10435-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="10435-398">Обратно в редакторе Unity, убедитесь, что **ShelfKeeper** класс выглядит как ниже:</span><span class="sxs-lookup"><span data-stu-id="10435-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Создание класса ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="10435-400">Если скрипт не имеет целевых объектов по ссылке (т. е. *даты (текст Mesh)* ), просто перетащите соответствующие объекты из **панели иерархии**, в целевой объект поля.</span><span class="sxs-lookup"><span data-stu-id="10435-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="10435-401">Ниже приведены сведения о работе, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="10435-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="10435-402">Откройте **точки Spawn** массива в **ShelfKeeper** компонента скрипта, щелкнув левой кнопкой мыши его.</span><span class="sxs-lookup"><span data-stu-id="10435-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="10435-403">Появится вызываемой подраздел **размер**, который указывает размер массива.</span><span class="sxs-lookup"><span data-stu-id="10435-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="10435-404">Тип **3** в текстовое поле рядом с полем **размер** и нажмите клавишу **ввод**, и три слота будет создан под.</span><span class="sxs-lookup"><span data-stu-id="10435-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="10435-405">В рамках **иерархии** разверните **отображения времени** объекта (с левой кнопкой мыши стрелку рядом с ним).</span><span class="sxs-lookup"><span data-stu-id="10435-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="10435-406">Далее щелкните ***Main Camera*** изнутри **иерархии**, так что **инспектор** его сведениями.</span><span class="sxs-lookup"><span data-stu-id="10435-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="10435-407">Выберите **главной камеры** в **панели иерархии**.</span><span class="sxs-lookup"><span data-stu-id="10435-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="10435-408">Перетащите **даты** и **время** объектов из **панели иерархии** для **текстовой даты** и **текста во время** Слоты в **инспектор** из **Main Camera** в **ShelfKeeper** компонента.</span><span class="sxs-lookup"><span data-stu-id="10435-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="10435-409">Перетащите **точки Spawn** из **панели иерархии** (под *полки* объект) для **3** **элемент**ссылаются на целевые объекты под **Spawn точки** массива, как показано на рисунке.</span><span class="sxs-lookup"><span data-stu-id="10435-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Создание класса ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="10435-411">Глава 9 — создать класс ProductPrediction</span><span class="sxs-lookup"><span data-stu-id="10435-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="10435-412">Далее нужно создать класс является **ProductPrediction** класса.</span><span class="sxs-lookup"><span data-stu-id="10435-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="10435-413">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="10435-413">This class is responsible for:</span></span>

-   <span data-ttu-id="10435-414">Запрос **службы машинного обучения** экземпляр, который предоставляет текущую дату и время.</span><span class="sxs-lookup"><span data-stu-id="10435-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="10435-415">Десериализации ответа JSON в полезных данных.</span><span class="sxs-lookup"><span data-stu-id="10435-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="10435-416">Интерпретации данных, получение 3 рекомендуемых продуктов.</span><span class="sxs-lookup"><span data-stu-id="10435-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="10435-417">Вызов **ShelfKeeper** методы для отображения данных в сцене класса.</span><span class="sxs-lookup"><span data-stu-id="10435-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="10435-418">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="10435-418">To create this class:</span></span>

1.  <span data-ttu-id="10435-419">Перейдите к **сценарии** папку в **панель проекта**.</span><span class="sxs-lookup"><span data-stu-id="10435-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="10435-420">Щелкните правой кнопкой мыши внутри папки **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="10435-420">Right-click inside the folder, **Create** > **C\# Script**.</span></span> <span data-ttu-id="10435-421">Вызовите сценарий **ProductPrediction**.</span><span class="sxs-lookup"><span data-stu-id="10435-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="10435-422">Дважды щелкните новый **ProductPrediction** скрипт, чтобы открыть его с **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="10435-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="10435-423">Если **обнаружено изменение файла** диалоговое окно появится, нажмите кнопку \***перезагрузить решение**.</span><span class="sxs-lookup"><span data-stu-id="10435-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="10435-424">Добавьте следующие пространства имен в начало класса ProductPrediction:</span><span class="sxs-lookup"><span data-stu-id="10435-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

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

6.  <span data-ttu-id="10435-425">Внутри **ProductPrediction** класса вставьте следующие два объекта, которые состоят из нескольких вложенных классов.</span><span class="sxs-lookup"><span data-stu-id="10435-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="10435-426">Эти классы используются для сериализации и десериализации JSON для службы машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="10435-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

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

7.  <span data-ttu-id="10435-427">Затем добавьте следующие переменные выше предыдущий код (таким образом, связанные с JSON, что код в нижней части сценария, кода, все остальные функции и выходом из способ):</span><span class="sxs-lookup"><span data-stu-id="10435-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

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
    > <span data-ttu-id="10435-428">Убедитесь, что для вставки **первичный ключ** и **конечную точку запрос ответ**, из портале машинного обучения, в переменные здесь.</span><span class="sxs-lookup"><span data-stu-id="10435-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="10435-429">Под изображениями Показать, где вам потребовалось бы ключ и конечную точку.</span><span class="sxs-lookup"><span data-stu-id="10435-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="10435-432">Вставьте этот код в **Start()** метод.</span><span class="sxs-lookup"><span data-stu-id="10435-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="10435-433">**Start()** метод вызывается при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="10435-433">The **Start()** method is called when the class initializes:</span></span>

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

9.  <span data-ttu-id="10435-434">Ниже приведен метод, который получает значение даты и времени из Windows и преобразует его в формат, который в нашем эксперименте машинного обучения можно использовать для сравнения с данными, хранящимися в таблице.</span><span class="sxs-lookup"><span data-stu-id="10435-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

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

10. <span data-ttu-id="10435-435">Вы можете **удалить** **Update()** метод, так как этот класс не будет его использовать.</span><span class="sxs-lookup"><span data-stu-id="10435-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="10435-436">Добавьте следующий метод, который будет взаимодействовать текущей даты и времени в конечной точке машинного обучения и получать ответ в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="10435-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

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

            // Serialise the request
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

12. <span data-ttu-id="10435-437">Добавьте следующий метод, который отвечает за десериализацию ответ в формате JSON и обмен данными результат десериализации для **ShelfKeeper** класса.</span><span class="sxs-lookup"><span data-stu-id="10435-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="10435-438">Это приведет к появлению имена из трех элементов, согласно прогнозу продавать наиболее в текущую дату и время.</span><span class="sxs-lookup"><span data-stu-id="10435-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="10435-439">Вставьте приведенный ниже код в **ProductPrediction** класс, ниже предыдущего метода.</span><span class="sxs-lookup"><span data-stu-id="10435-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

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

13. <span data-ttu-id="10435-440">Сохранить **Visual Studio** и вернитесь к **Unity**.</span><span class="sxs-lookup"><span data-stu-id="10435-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="10435-441">Перетащите **ProductPrediction** класса скрипт из **сценарий** папку, на **Main Camera** объекта.</span><span class="sxs-lookup"><span data-stu-id="10435-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="10435-442">Сохраните сцену и проект **файл** >  ***сохранить сцену* / *файл***   >  **Сохранить проект**.</span><span class="sxs-lookup"><span data-stu-id="10435-442">Save your scene and project **File** > ***Save Scene* / *File*** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="10435-443">Глава 10 - выполнить сборку решения универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="10435-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="10435-444">Пришло время выполнить сборку проекта в качестве решения UWP может выполняться как отдельное приложение.</span><span class="sxs-lookup"><span data-stu-id="10435-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="10435-445">Для сборки:</span><span class="sxs-lookup"><span data-stu-id="10435-445">To Build:</span></span>

1.  <span data-ttu-id="10435-446">Сохранить текущую сцену, щелкнув **файл** **сохранить сцены**.</span><span class="sxs-lookup"><span data-stu-id="10435-446">Save the current scene by clicking on **File** **Save Scenes**.</span></span>

2.  <span data-ttu-id="10435-447">Перейдите к **файл** **параметры сборки**</span><span class="sxs-lookup"><span data-stu-id="10435-447">Go to **File** **Build Settings**</span></span>

3.  <span data-ttu-id="10435-448">Проверьте поле, называемое **Unity C\# проекты** (это важно, так как он позволит вам изменить классы, после завершения сборки).</span><span class="sxs-lookup"><span data-stu-id="10435-448">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="10435-449">Щелкните **Добавление открытых сцен**,</span><span class="sxs-lookup"><span data-stu-id="10435-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="10435-450">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="10435-450">Click **Build**.</span></span>

    ![Выполните сборку решения универсальной платформы Windows](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="10435-452">Вам будет предложено выбрать папку, где требуется выполнить сборку решения.</span><span class="sxs-lookup"><span data-stu-id="10435-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="10435-453">Создание **ПОСТРОЕНИЯ** папку и в этой папке создайте другую папку с соответствующим именем, по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="10435-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="10435-454">Щелкните новую папку и нажмите кнопку **Выбор папки**, чтобы начать построение в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="10435-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Выполните сборку решения универсальной платформы Windows](images/AzureLabs-Lab7-55.png)

    ![Выполните сборку решения универсальной платформы Windows](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="10435-457">Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).</span><span class="sxs-lookup"><span data-stu-id="10435-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="10435-458">Глава 11 - развертывания приложения</span><span class="sxs-lookup"><span data-stu-id="10435-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="10435-459">Для развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="10435-459">To deploy your application:</span></span>

1.  <span data-ttu-id="10435-460">Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="10435-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="10435-461">Откройте Visual Studio вам потребуется восстановить пакеты NuGet, который можно сделать с помощью щелкнув MachineLearningLab_Build решения, в обозревателе решений (находится справа от Visual Studio) щелкните правой кнопкой мыши и выбрав восстановить пакеты NuGet.</span><span class="sxs-lookup"><span data-stu-id="10435-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Добавьте пакеты NuGet](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="10435-463">В списке выберите конфигурацию решения **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="10435-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="10435-464">В платформу решения, выберите **x86**, **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="10435-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="10435-465">Для Microsoft HoloLens, может быть проще устанавливать равным *удаленный компьютер*, таким образом, не связанном устройстве на компьютер.</span><span class="sxs-lookup"><span data-stu-id="10435-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="10435-466">Однако необходимо будет выполнить следующее:</span><span class="sxs-lookup"><span data-stu-id="10435-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="10435-467">Знать **IP-адрес** из HoloLens, которую можно найти в *параметры > сеть и Интернет > Wi-Fi > Дополнительно*; IPv4 — это адрес, следует использовать.</span><span class="sxs-lookup"><span data-stu-id="10435-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="10435-468">Убедитесь, **режим разработчика** — **на**; найдено в *параметры > обновление и безопасность > для разработчиков*.</span><span class="sxs-lookup"><span data-stu-id="10435-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Добавьте пакеты NuGet](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="10435-470">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на вашем ПК.</span><span class="sxs-lookup"><span data-stu-id="10435-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="10435-471">Приложения появятся в списке установленных приложений, Готово к запуску.</span><span class="sxs-lookup"><span data-stu-id="10435-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="10435-472">При запуске приложения смешанной реальности, вы увидите bench, которая была создана в сцене Unity, и от инициализации, будут выбираться данные, которые можно настроить в Azure.</span><span class="sxs-lookup"><span data-stu-id="10435-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="10435-473">Данные, которые будут десериализованы в вашем приложении, и три лучших результатов для текущей датой и временем будет предоставляться визуально три модели на bench.</span><span class="sxs-lookup"><span data-stu-id="10435-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="10435-474">Готового приложения машинного обучения</span><span class="sxs-lookup"><span data-stu-id="10435-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="10435-475">Поздравляем, вы создали приложение смешанной реальности, которое использует машинное обучение Azure для прогнозирования данных и их отображения на сцены.</span><span class="sxs-lookup"><span data-stu-id="10435-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Добавьте пакеты NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="10435-477">Упражнение</span><span class="sxs-lookup"><span data-stu-id="10435-477">Exercise</span></span>

<span data-ttu-id="10435-478">**Упражнение 1**</span><span class="sxs-lookup"><span data-stu-id="10435-478">**Exercise 1**</span></span>

<span data-ttu-id="10435-479">Поэкспериментируйте с порядком сортировки, приложения и имеют три нижних прогнозы отображаются на полки, как эти данные потенциально полезным также.</span><span class="sxs-lookup"><span data-stu-id="10435-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="10435-480">**Упражнение 2**</span><span class="sxs-lookup"><span data-stu-id="10435-480">**Exercise 2**</span></span>

<span data-ttu-id="10435-481">С помощью **таблицы Azure** Заполните новую таблицу с информацией о погоде и создайте новый эксперимент, используя данные.</span><span class="sxs-lookup"><span data-stu-id="10435-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
