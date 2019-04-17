---
title: Г-н и Azure 307 - машинного обучения
description: Выполните этот курс, чтобы узнать, как реализовать приложение смешанной реальности студии машинного обучения Azure.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, руководства, api, машинное обучение, ml, студия машинного обучения, hololens, насыщенные, виртуальной реальности
ms.openlocfilehash: 726a6cce91d46ad878f8502381d085fb979ac72a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600279"
---
>[!NOTE]
><span data-ttu-id="ee048-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="ee048-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ee048-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="ee048-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ee048-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ee048-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ee048-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="ee048-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ee048-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ee048-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ee048-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="ee048-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="ee048-110">Г-н и Azure 307: Машинное обучение</span><span class="sxs-lookup"><span data-stu-id="ee048-110">MR and Azure 307: Machine learning</span></span>

![конечный продукт-запуск](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="ee048-112">В рамках этого курса вы узнаете, как добавить возможности машинного обучения (ML) приложение смешанной реальности, с помощью студии машинного обучения Azure.</span><span class="sxs-lookup"><span data-stu-id="ee048-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="ee048-113">*Студия машинного обучения Azure* — это служба Майкрософт, которая предоставляет разработчикам множество алгоритмов машинного обучения, которые могут помочь с входных данных, выходных данных, подготовки и визуализации.</span><span class="sxs-lookup"><span data-stu-id="ee048-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="ee048-114">Из этих компонентов то существует возможность разработки эксперимента прогнозной аналитики, выполнить на ней итерацию и использовать ее для обучения модели.</span><span class="sxs-lookup"><span data-stu-id="ee048-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="ee048-115">После обучения, можно сделать модель operational в облаке Azure, таким образом, чтобы его можно затем оценки новых данных.</span><span class="sxs-lookup"><span data-stu-id="ee048-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="ee048-116">Дополнительные сведения см. в статье [странице студии машинного обучения Azure](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="ee048-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="ee048-117">Оформили этот курс, вы получите приложение иммерсивных гарнитуры смешанной реальности и будет узнали, как выполнить следующие:</span><span class="sxs-lookup"><span data-stu-id="ee048-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="ee048-118">Создать таблицу с данными продаж для *студии машинного обучения Azure* портала и проектирования алгоритм для прогнозирования будущих продаж популярных элементов.</span><span class="sxs-lookup"><span data-stu-id="ee048-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="ee048-119">Создание **проекта Unity**, который может получать и интерпретировать данные прогноза из службы машинного Обучения.</span><span class="sxs-lookup"><span data-stu-id="ee048-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="ee048-120">Отобразить данные прогнозирование визуально в **проекта Unity**, до предоставления самыми популярными материалами продаж на полке.</span><span class="sxs-lookup"><span data-stu-id="ee048-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="ee048-121">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="ee048-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ee048-122">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="ee048-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="ee048-123">Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="ee048-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="ee048-124">Этот курс — это автономное руководство, которые не предусматривают любых других смешанной реальности лабораторий, напрямую.</span><span class="sxs-lookup"><span data-stu-id="ee048-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="ee048-125">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="ee048-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ee048-126">Курс</span><span class="sxs-lookup"><span data-stu-id="ee048-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ee048-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ee048-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ee048-128"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="ee048-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ee048-129">Г-н и Azure 307: Машинное обучение</span><span class="sxs-lookup"><span data-stu-id="ee048-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="ee048-130">✔️</span><span class="sxs-lookup"><span data-stu-id="ee048-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ee048-131">✔️</span><span class="sxs-lookup"><span data-stu-id="ee048-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ee048-132">Хотя этот курс основное внимание уделяется Windows Mixed Reality иммерсивную (VR), можно также применить полученные знания в этом курсе для Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ee048-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ee048-133">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ee048-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ee048-134">При использовании HoloLens, вы можете заметить некоторые echo во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="ee048-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ee048-135">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="ee048-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ee048-136">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="ee048-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ee048-137">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="ee048-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ee048-138">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства статье](install-the-tools.md), хотя следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .</span><span class="sxs-lookup"><span data-stu-id="ee048-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ee048-139">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="ee048-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ee048-140">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="ee048-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ee048-141">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="ee048-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ee048-142">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="ee048-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ee048-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="ee048-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ee048-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ee048-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ee048-145">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="ee048-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ee048-146">Доступ к Интернету для настройки Azure и получения данных машинного Обучения</span><span class="sxs-lookup"><span data-stu-id="ee048-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ee048-147">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="ee048-147">Before you start</span></span>

<span data-ttu-id="ee048-148">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="ee048-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="ee048-149">Глава 1 - установки учетная запись хранения Azure</span><span class="sxs-lookup"><span data-stu-id="ee048-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="ee048-150">Чтобы использовать Azure Translator API, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="ee048-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="ee048-151">Войдите в [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ee048-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ee048-152">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="ee048-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ee048-153">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="ee048-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ee048-154">После входа в систему щелкните **учетные записи хранения** в меню слева.</span><span class="sxs-lookup"><span data-stu-id="ee048-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="ee048-156">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="ee048-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="ee048-157">На **учетные записи хранения** , щелкните на **добавить**.</span><span class="sxs-lookup"><span data-stu-id="ee048-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="ee048-159">В **создать учетную запись хранения** панели:</span><span class="sxs-lookup"><span data-stu-id="ee048-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="ee048-160">Вставить **имя** для вашей учетной записи, помните, это поле принимает только цифры и строчные буквы.</span><span class="sxs-lookup"><span data-stu-id="ee048-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="ee048-161">Для **модели развертывания,** выберите **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="ee048-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="ee048-162">Для **тип учетной записи**выберите **хранилища (общего назначения версии 1)**.</span><span class="sxs-lookup"><span data-stu-id="ee048-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="ee048-163">Для **производительности**выберите **стандартный**.</span><span class="sxs-lookup"><span data-stu-id="ee048-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="ee048-164">Для **репликации** выберите **Read-access геоизбыточного хранилища (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="ee048-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="ee048-165">Оставьте **требуется безопасное перемещение** как **отключено**.</span><span class="sxs-lookup"><span data-stu-id="ee048-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="ee048-166">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="ee048-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="ee048-167">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="ee048-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ee048-168">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="ee048-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ee048-169">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="ee048-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="ee048-170">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="ee048-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="ee048-171">Определить **расположение** для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="ee048-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ee048-172">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="ee048-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ee048-173">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="ee048-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="ee048-174">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="ee048-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="ee048-176">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="ee048-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="ee048-177">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="ee048-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Настройка учетной записи хранения Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="ee048-179">Глава 2 - студии машинного обучения Azure</span><span class="sxs-lookup"><span data-stu-id="ee048-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="ee048-180">Чтобы использовать *машинного обучения Azure*, необходимо настроить экземпляр службы машинного обучения, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="ee048-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="ee048-181">На портале Azure щелкните **New** в левом верхнем углу, а поиск **рабочая область студии машинного обучения**, нажмите клавишу **ввод**.</span><span class="sxs-lookup"><span data-stu-id="ee048-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="ee048-183">Новая страница будет предоставить описание **рабочая область студии машинного обучения** службы.</span><span class="sxs-lookup"><span data-stu-id="ee048-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="ee048-184">В нижней левой части этого запроса, нажмите кнопку **создать** кнопку, чтобы создать ассоциацию с этой службой.</span><span class="sxs-lookup"><span data-stu-id="ee048-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="ee048-185">Когда вы перейдете на **создать**, будет отображаться панель, где необходимо предоставить некоторые сведения о новой **службы студии машинного обучения**:</span><span class="sxs-lookup"><span data-stu-id="ee048-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="ee048-186">Вставить нужный **имя рабочей области** для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="ee048-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="ee048-187">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="ee048-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="ee048-188">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="ee048-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ee048-189">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="ee048-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ee048-190">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как многому) в разделе общей группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="ee048-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="ee048-191">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="ee048-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="ee048-192">Определить **расположение** для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="ee048-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ee048-193">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="ee048-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ee048-194">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="ee048-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="ee048-195">Следует использовать ту же группу ресурсов, которую вы использовали для создания хранилища Azure в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="ee048-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="ee048-196">Для **учетной записи хранения** щелкните **использовать существующий**, затем щелкните раскрывающееся меню и щелкните **учетной записи хранения** созданный в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="ee048-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="ee048-197">Выберите соответствующий **ценовой категории рабочей области** автоматически, в раскрывающемся меню.</span><span class="sxs-lookup"><span data-stu-id="ee048-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="ee048-198">В рамках **план веб-службы** щелкните **создать** **новых,** в текстовом поле введите ее имя.</span><span class="sxs-lookup"><span data-stu-id="ee048-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="ee048-199">Из **ценовой план веб-службы** выберите Ценовая категория по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="ee048-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="ee048-200">Разработки и тестирования уровень **DEVTEST стандартный** должны быть доступны вам бесплатно.</span><span class="sxs-lookup"><span data-stu-id="ee048-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="ee048-201">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="ee048-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="ee048-202">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="ee048-202">Click **Create**.</span></span>

        ![Студия машинного обучения Azure](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="ee048-204">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="ee048-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="ee048-205">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="ee048-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="ee048-207">Щелкните уведомление, чтобы изучить ваш новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="ee048-207">Click on the notification to explore your new Service instance.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="ee048-209">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="ee048-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="ee048-210">На странице отображается, в разделе **Дополнительные ссылки** щелкните **запуска студии машинного обучения**, который будет направлять в браузере **студии машинного обучения** портал.</span><span class="sxs-lookup"><span data-stu-id="ee048-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="ee048-212">Используйте **Sign In** кнопки в правом верхнем углу или в центре, чтобы войти в студию машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="ee048-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Студия машинного обучения Azure](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="ee048-214">Глава 3 - студии машинного обучения: Настройка набора данных</span><span class="sxs-lookup"><span data-stu-id="ee048-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="ee048-215">Одним из способов работы алгоритмов машинного обучения по анализа существующих данных, а затем попытаться спрогнозировать будущие результаты на основе существующего набора данных.</span><span class="sxs-lookup"><span data-stu-id="ee048-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="ee048-216">Это обычно означает, что у вас есть, тем лучше алгоритм будет в прогнозировании будущих результатов более существующих данных.</span><span class="sxs-lookup"><span data-stu-id="ee048-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="ee048-217">Образец таблицы вам предоставляется, этот курс вызывается [ProductsTableCSV и может быть скачан здесь](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="ee048-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee048-218">Выше ZIP-файл содержит оба **ProductsTableCSV** и **.unitypackage**, которые потребуются в [Глава 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="ee048-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="ee048-219">Этот пакет также предоставляется в рамках соответствующей главы, хотя отдельные CSV-файл.</span><span class="sxs-lookup"><span data-stu-id="ee048-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="ee048-220">Этот пример набора данных содержит запись популярных объектов на каждый час каждый день 2017 года.</span><span class="sxs-lookup"><span data-stu-id="ee048-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Студия машинного обучения: Настройка набора данных](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="ee048-222">Например, на 1 день 2017 г., в 13: 00 (час 13), центр ознакомительного программного обеспечения элемент был соль и Перец.</span><span class="sxs-lookup"><span data-stu-id="ee048-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="ee048-223">Этот пример таблицы содержит 9998 записи.</span><span class="sxs-lookup"><span data-stu-id="ee048-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="ee048-224">Вернитесь к **студии машинного обучения** портала, и добавить эту таблицу как **набора данных** для вашей машинного Обучения.</span><span class="sxs-lookup"><span data-stu-id="ee048-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="ee048-225">Это можно сделать, щелкнув **+ создать** кнопку в левом нижнем углу экрана.</span><span class="sxs-lookup"><span data-stu-id="ee048-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Студия машинного обучения: Настройка набора данных](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="ee048-227">Раздел будет снизу и в наличии панели навигации слева.</span><span class="sxs-lookup"><span data-stu-id="ee048-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="ee048-228">Нажмите кнопку **набора данных**, а затем в правой части, **из локального файла**.</span><span class="sxs-lookup"><span data-stu-id="ee048-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Студия машинного обучения: Настройка набора данных](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="ee048-230">Передать новый **набора данных** , сделав следующее:</span><span class="sxs-lookup"><span data-stu-id="ee048-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="ee048-231">Будет открыто окно отправки, где вы можете **Обзор** жестком диске для нового набора данных.</span><span class="sxs-lookup"><span data-stu-id="ee048-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Студия машинного обучения: Настройка набора данных](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="ee048-233">После выбора и обратно в окне передачи, оставьте флажок снятом.</span><span class="sxs-lookup"><span data-stu-id="ee048-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="ee048-234">В текстовом поле ниже, введите **ProductsTableCSV.csv** как имя для набора данных (хотя автоматически добавляются).</span><span class="sxs-lookup"><span data-stu-id="ee048-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="ee048-235">С помощью раскрывающееся меню для **тип**выберите **универсальный CSV-файл с заголовком (CSV)**.</span><span class="sxs-lookup"><span data-stu-id="ee048-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="ee048-236">Нажмите клавишу деления в правом нижнем углу окна передачи и **набора данных** будут отправлены.</span><span class="sxs-lookup"><span data-stu-id="ee048-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="ee048-237">Глава 4 – студии машинного обучения: Эксперимент</span><span class="sxs-lookup"><span data-stu-id="ee048-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="ee048-238">Перед созданием машинного обучения системы, необходимо будет эксперимент, проверяемый на теории о своих данных.</span><span class="sxs-lookup"><span data-stu-id="ee048-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="ee048-239">С результатами вы будете знать, если вам нужно больше данных, или в том случае, если нет никакой корреляции между данными и возможный результат.</span><span class="sxs-lookup"><span data-stu-id="ee048-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="ee048-240">Чтобы приступить к созданию эксперимента:</span><span class="sxs-lookup"><span data-stu-id="ee048-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="ee048-241">Снова щелкните **+ создать** кнопку в левом нижнем углу страницы, а затем **эксперимента** > **пустой эксперимент**.</span><span class="sxs-lookup"><span data-stu-id="ee048-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="ee048-243">Новая страница будет отображаться с пустой эксперимент:</span><span class="sxs-lookup"><span data-stu-id="ee048-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="ee048-244">На панели слева разверните в \**сохраненные наборы данных* > \* Мои наборы данных \*\* и перетащите **ProductsTableCSV** в **эксперимента**.</span><span class="sxs-lookup"><span data-stu-id="ee048-244">From the panel on the left expand \**Saved Datasets* > \*My Datasets\*\* and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="ee048-246">На панели слева разверните **преобразования данных** > **выборка и разбиение**.</span><span class="sxs-lookup"><span data-stu-id="ee048-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="ee048-247">Затем перетащите **разбиение данных** элемент в **эксперимента**.</span><span class="sxs-lookup"><span data-stu-id="ee048-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="ee048-248">Элемент разделения данных будет разделить набор данных на две части.</span><span class="sxs-lookup"><span data-stu-id="ee048-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="ee048-249">Одной из частей будет использоваться для обучения алгоритма машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="ee048-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="ee048-250">Вторая часть будет использоваться для оценки точности алгоритма создан.</span><span class="sxs-lookup"><span data-stu-id="ee048-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="ee048-252">На панели справа (во время разбиения данных выбран элемент на холсте) изменить **доля строк в первый выходной набор данных** для **0,7**.</span><span class="sxs-lookup"><span data-stu-id="ee048-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="ee048-253">Это будет разбить данные на две части, первая часть будет 70% данных, а вторая часть будет оставшиеся 30%.</span><span class="sxs-lookup"><span data-stu-id="ee048-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="ee048-254">Чтобы убедиться, что данные разбиваются случайным образом, убедитесь, что **случайного разбиения** снимайте флажок.</span><span class="sxs-lookup"><span data-stu-id="ee048-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="ee048-256">Перетащите подключение из основание системы счисления **ProductsTableCSV** элемента на холсте вверху элемента разделения данных.</span><span class="sxs-lookup"><span data-stu-id="ee048-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="ee048-257">Это будет подключить элементы и отправлять **ProductsTableCSV** выходные данные набора данных (данные) для разделения входных данных.</span><span class="sxs-lookup"><span data-stu-id="ee048-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="ee048-259">В **экспериментов** на левой панели, разверните узел \**машинного обучения* > \* Train **. Перетащите **Обучение модели \*\* элемента out в на холст эксперимента.</span><span class="sxs-lookup"><span data-stu-id="ee048-259">In the **Experiments** panel on the left side, expand \**Machine Learning* > \*Train **. Drag the **Train Model\*\* item out in to the Experiment canvas.</span></span> <span data-ttu-id="ee048-260">Холст должен выглядеть так же, как ниже.</span><span class="sxs-lookup"><span data-stu-id="ee048-260">Your canvas should look the same as the below.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="ee048-262">Из ***нижнем левом углу*** из **разбиение данных** элементов перетащите соединение **вверху справа** из **Обучение модели** элемента.</span><span class="sxs-lookup"><span data-stu-id="ee048-262">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="ee048-263">Первого разбиения 70% из набора данных будет использоваться Обучение модели для обучения алгоритму.</span><span class="sxs-lookup"><span data-stu-id="ee048-263">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="ee048-265">Выберите **Обучение модели** элемент на холсте, а также на **свойства** панели (в правой части окна браузера) выберите **запустить средство выбора столбцов**  кнопки.</span><span class="sxs-lookup"><span data-stu-id="ee048-265">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="ee048-266">В текстовом поле введите **продукта** и нажмите клавишу **ввод**, *продукта* будет установлен в качестве столбца для обучения прогнозов.</span><span class="sxs-lookup"><span data-stu-id="ee048-266">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="ee048-267">После этого щелкните **делений** в нижнем правом углу, чтобы закрыть диалоговое окно выбора.</span><span class="sxs-lookup"><span data-stu-id="ee048-267">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="ee048-269">Вы собираетесь обучения **Мультиклассовая логистическая Регрессия** алгоритм для прогнозирования наиболее популярное **продукта** зависимости от часа дня и даты.</span><span class="sxs-lookup"><span data-stu-id="ee048-269">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="ee048-270">Это выходит за рамки этого документа, чтобы подробно описывается различных алгоритмов, предоставляемых студией машинного обучения Azure, однако вы подробнее можно узнать из [машины обучения Памятка по алгоритмам](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="ee048-270">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="ee048-271">Из панели элементов эксперимента в левой части разверните \*\**машинного обучения* > *Initialize Model* > \* классификации \***и перетащите **многоклассовая классификация " Алгоритм логистической регрессии \*\* элементов на холст эксперимента.</span><span class="sxs-lookup"><span data-stu-id="ee048-271">From the experiment items panel on the left, expand \*\**Machine Learning* > *Initialize Model* > \*Classification\***, and drag the **Multiclass Logistic Regression\*\* item on to the experiment canvas.</span></span>

13. <span data-ttu-id="ee048-272">Соедините выход, в нижней части **Мультиклассовая логистическая Регрессия**, на верхний левый вход **Обучение модели** элемента.</span><span class="sxs-lookup"><span data-stu-id="ee048-272">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="ee048-274">В списке элементов эксперимента на панели слева разверните узел \**машинного обучения* > \* Оценка**и перетащите **оценка модели \*\* элементов на холст.</span><span class="sxs-lookup"><span data-stu-id="ee048-274">In list of experiment items in the panel on the left, expand \**Machine Learning* > \*Score **, and drag the **Score Model\*\* item on to the canvas.</span></span>

15. <span data-ttu-id="ee048-275">Соедините выход, в нижней части **Обучение модели**, на верхний левый вход **оценка модели**.</span><span class="sxs-lookup"><span data-stu-id="ee048-275">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="ee048-276">Соедините выход из нижнего правого **разбиение данных**, на верхний правый вход \**Score Model* элемента \*.</span><span class="sxs-lookup"><span data-stu-id="ee048-276">Connect the bottom-right output from **Split Data**, to the top-right input of the \**Score Model* item\*.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="ee048-278">В списке **эксперимента** элементы на панели слева разверните \*\**машинного обучения* > \* Evaluate \***и перетащите **оценки модели \*\* элементов на холст.</span><span class="sxs-lookup"><span data-stu-id="ee048-278">In the list of **Experiment** items in the panel on the left, expand \*\**Machine Learning* > \*Evaluate\***, and drag the **Evaluate Model\*\* item onto the canvas.</span></span>

18. <span data-ttu-id="ee048-279">Соедините выход из **Score Model** на верхний левый вход **Evaluate Model**.</span><span class="sxs-lookup"><span data-stu-id="ee048-279">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="ee048-281">Вы создали свой первый эксперимент обучения машины.</span><span class="sxs-lookup"><span data-stu-id="ee048-281">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="ee048-282">Теперь можно сохранить и запустить эксперимент.</span><span class="sxs-lookup"><span data-stu-id="ee048-282">You can now save and run the experiment.</span></span> <span data-ttu-id="ee048-283">В меню в нижней части страницы щелкните **Сохранить** кнопку, чтобы сохранить свой эксперимент и нажмите кнопку **запуска** запуск эксперимента.</span><span class="sxs-lookup"><span data-stu-id="ee048-283">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="ee048-285">Вы увидите **состояние** в верхней правой части холста эксперимента.</span><span class="sxs-lookup"><span data-stu-id="ee048-285">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="ee048-286">Подождите несколько секунд для эксперимента завершить.</span><span class="sxs-lookup"><span data-stu-id="ee048-286">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="ee048-287">Если у вас есть набор данных больших (реальном мире) вполне вероятно, что эксперимента может занять часов для выполнения.</span><span class="sxs-lookup"><span data-stu-id="ee048-287">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="ee048-289">Щелкните правой кнопкой мыши **Evaluate Model** элемент на холсте и из контекстного меню при наведении указателя мыши мыши над **результаты оценки**, а затем выберите **визуализировать**.</span><span class="sxs-lookup"><span data-stu-id="ee048-289">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="ee048-291">Результаты оценки отображаются отображение прогнозируемых выходных данных и фактические результаты.</span><span class="sxs-lookup"><span data-stu-id="ee048-291">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="ee048-292">При этом используется 30% исходного набора данных, который был ранее, разделение для оценки модели.</span><span class="sxs-lookup"><span data-stu-id="ee048-292">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="ee048-293">Вы увидите, что результаты не отлично, в идеале вам будет иметь наибольший номер в каждой строке размещения выделенный элемент в столбцах.</span><span class="sxs-lookup"><span data-stu-id="ee048-293">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="ee048-295">Закрыть **результаты**.</span><span class="sxs-lookup"><span data-stu-id="ee048-295">Close the **Results**.</span></span>

24. <span data-ttu-id="ee048-296">В использовании обученной модели машинного обучения, необходимо предоставлять его как **веб-службы**.</span><span class="sxs-lookup"><span data-stu-id="ee048-296">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="ee048-297">Чтобы сделать это, щелкните **настроить веб-службу** меню в меню в нижней части страницы и щелкните на **прогнозной веб-службы**.</span><span class="sxs-lookup"><span data-stu-id="ee048-297">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="ee048-299">Будет создана новая вкладка, и обучение модели объединяются для создания новой веб-службы.</span><span class="sxs-lookup"><span data-stu-id="ee048-299">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="ee048-300">В меню в нижней части страницы щелкните **Сохранить**, затем нажмите кнопку **запуска**.</span><span class="sxs-lookup"><span data-stu-id="ee048-300">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span><span data-ttu-id="ee048-301"> Вы увидите состояние обновления в правом верхнем углу холста эксперимента.</span><span class="sxs-lookup"><span data-stu-id="ee048-301"> You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="ee048-303">После завершения работы, **Deploy Web Service** кнопка будет отображаться в нижней части страницы.</span><span class="sxs-lookup"><span data-stu-id="ee048-303">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="ee048-304">Вы готовы к развертыванию веб-службы.</span><span class="sxs-lookup"><span data-stu-id="ee048-304">You are ready to deploy the web service.</span></span> <span data-ttu-id="ee048-305">Нажмите кнопку **Deploy Web Service** (классической) в меню в нижней части страницы.</span><span class="sxs-lookup"><span data-stu-id="ee048-305">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="ee048-307">Ваш браузер может запросить чтобы разрешить всплывающее окно, в которой следует **Разрешить**, хотя может потребоваться нажать **Deploy Web Service** опять же, если на странице развертывание не отображается.</span><span class="sxs-lookup"><span data-stu-id="ee048-307">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="ee048-308">После создания эксперимента вы будете перенаправлены к **панели мониторинга** страницы, где у вас будет вашей **ключ API** отображается.</span><span class="sxs-lookup"><span data-stu-id="ee048-308">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="ee048-309">Скопируйте его в Блокнот в данный момент, он потребуется в коде очень скоро.</span><span class="sxs-lookup"><span data-stu-id="ee048-309">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="ee048-310">Когда вы заметили ключ API, нажмите кнопку **запрос/ОТВЕТ** кнопку в **конечная точка по умолчанию** разделе под ключ.</span><span class="sxs-lookup"><span data-stu-id="ee048-310">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="ee048-312">Если щелкнуть теста на этой странице можно ввести входные данные и просмотреть выходные данные.</span><span class="sxs-lookup"><span data-stu-id="ee048-312">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="ee048-313">Введите **день** и **час**.</span><span class="sxs-lookup"><span data-stu-id="ee048-313">Enter the **day** and **hour**.</span></span> <span data-ttu-id="ee048-314">Оставьте **продукта** запись пустым.</span><span class="sxs-lookup"><span data-stu-id="ee048-314">Leave the **product** entry blank.</span></span> <span data-ttu-id="ee048-315">Нажмите кнопку **Подтверждение** кнопки.</span><span class="sxs-lookup"><span data-stu-id="ee048-315">Then click the **Confirm** button.</span></span><span data-ttu-id="ee048-316"> JSON, представляющее вероятность каждого продукта, что выбор будут показаны результаты в нижней части страницы.</span><span class="sxs-lookup"><span data-stu-id="ee048-316"> The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="ee048-317">Новый веб-страницы откроется, отображение инструкции и примеры о структуре запроса, требующегося студии машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="ee048-317">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="ee048-318">Копировать **URI запроса** отображаются на этой странице в вашей Блокнот.</span><span class="sxs-lookup"><span data-stu-id="ee048-318">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="ee048-320">Теперь вы создали это система, обеспечивающие, скорее всего, для продажи продукта на основе исторических приобретения данных, соотносятся с временем дня года и машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="ee048-320">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="ee048-321">Чтобы вызвать веб-службы, вам потребуется URL-адрес конечной точки службы и ключ API для службы.</span><span class="sxs-lookup"><span data-stu-id="ee048-321">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="ee048-322">Щелкните **Consume** вкладки в верхней строке меню.</span><span class="sxs-lookup"><span data-stu-id="ee048-322">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="ee048-323">**Потребления** сведения будут отображаться сведения, необходимо будет вызывать веб-службы из кода.</span><span class="sxs-lookup"><span data-stu-id="ee048-323">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="ee048-324">Сделайте копию **первичный ключ** и **запрос-ответ** URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="ee048-324">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="ee048-325">Они потребуются в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="ee048-325">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="ee048-326">Глава 5 - Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="ee048-326">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="ee048-327">Настройка и проверка вашего смешанной реальности гарнитура Иммерсивных.</span><span class="sxs-lookup"><span data-stu-id="ee048-327">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="ee048-328">Вы будете **не** требуются контроллеры движения курс с демороликами.</span><span class="sxs-lookup"><span data-stu-id="ee048-328">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="ee048-329">Если вам нужна поддерживает настройку Иммерсивных гарнитура, нажмите кнопку [здесь](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="ee048-329">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="ee048-330">Откройте **Unity** и создайте новый проект Unity с именем **MR\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="ee048-330">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="ee048-331">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="ee048-331">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="ee048-332">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ee048-332">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ee048-333">Перейдите к ***изменить* > *предпочтения*** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="ee048-333">Go to ***Edit* > *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ee048-334">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="ee048-334">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ee048-335">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="ee048-335">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="ee048-336">Перейдите к ***файл* > *параметры построения*** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув ***переключить платформу*** кнопки.</span><span class="sxs-lookup"><span data-stu-id="ee048-336">Next, go to ***File* > *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="ee048-337">Также убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="ee048-337">Also make sure that:</span></span>

    1.  <span data-ttu-id="ee048-338">**Целевое устройство** присваивается **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="ee048-338">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="ee048-339">Microsoft HoloLens, задайте **целевое устройство** для *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="ee048-339">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="ee048-340">**Тип сборки** присваивается **D3D**.</span><span class="sxs-lookup"><span data-stu-id="ee048-340">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="ee048-341">**Пакет SDK для** присваивается **самую новую установленную**.</span><span class="sxs-lookup"><span data-stu-id="ee048-341">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="ee048-342">**Версия Visual Studio** присваивается **самую новую установленную**.</span><span class="sxs-lookup"><span data-stu-id="ee048-342">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="ee048-343">**Сборка и запуск** присваивается **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="ee048-343">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="ee048-344">Не беспокоиться о настройке **сцены** прямо сейчас, как они предоставляются в более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="ee048-344">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="ee048-345">Остальные параметры следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="ee048-345">The remaining settings should be left as default for now.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="ee048-347">В **параметры построения** щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где **инспектор** находится.</span><span class="sxs-lookup"><span data-stu-id="ee048-347">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="ee048-348">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="ee048-348">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ee048-349">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="ee048-349">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ee048-350">**Сценарии** **версии среды выполнения** должно быть **экспериментальные** (.NET 4.6 эквивалент)</span><span class="sxs-lookup"><span data-stu-id="ee048-350">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="ee048-351">**Создание сценариев серверной части** должно быть ***.NET***</span><span class="sxs-lookup"><span data-stu-id="ee048-351">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="ee048-352">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="ee048-352">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="ee048-354">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="ee048-354">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="ee048-355">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="ee048-355">**InternetClient**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="ee048-357">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется</span><span class="sxs-lookup"><span data-stu-id="ee048-357">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="ee048-359">Вернитесь в **параметры построения** *Unity C#*  проектов больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="ee048-359">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="ee048-360">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="ee048-360">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="ee048-361">Сохраните проект (**ФАЙЛ > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="ee048-361">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="ee048-362">Глава 6 - Импорт пакета MLProducts Unity</span><span class="sxs-lookup"><span data-stu-id="ee048-362">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="ee048-363">Для этого курса необходимо скачать пакет средств Unity [ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="ee048-363">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="ee048-364">Этот пакет поставляется со сцены, и объекты, предварительно созданные, вы сможете сосредоточиться на начало его все работает.</span><span class="sxs-lookup"><span data-stu-id="ee048-364">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="ee048-365">**ShelfKeeper** предоставляется скрипт, но содержит только открытые переменные, для установки структуры сцены.</span><span class="sxs-lookup"><span data-stu-id="ee048-365">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="ee048-366">Необходимо будет сделать все остальные разделы.</span><span class="sxs-lookup"><span data-stu-id="ee048-366">You will need to do all other sections.</span></span> 

<span data-ttu-id="ee048-367">Для импорта этого пакета:</span><span class="sxs-lookup"><span data-stu-id="ee048-367">To import this package:</span></span>

1.  <span data-ttu-id="ee048-368">С помощью панели мониторинга Unity перед глазами, щелкните **активы** в меню в верхней части экрана, нажмите кнопку **Импорт пакета, пользовательского пакета**.</span><span class="sxs-lookup"><span data-stu-id="ee048-368">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Импорт пакета MLProducts Unity](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="ee048-370">Используйте средство выбора файлов для выбора **Azure-MR-307.unitypackage** пакета и нажмите кнопку **откройте**.</span><span class="sxs-lookup"><span data-stu-id="ee048-370">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="ee048-371">Список компонентов для этого ресурса будет отображаться пользователю.</span><span class="sxs-lookup"><span data-stu-id="ee048-371">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="ee048-372">Подтверждение импорта, щелкнув **импорта**.</span><span class="sxs-lookup"><span data-stu-id="ee048-372">Confirm the import by clicking **Import**.</span></span>

    ![Импорт пакета MLProducts Unity](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="ee048-374">После его завершения импорта можно заметить, что некоторые новые папки публиковались в игру на Unity **панель проекта**.</span><span class="sxs-lookup"><span data-stu-id="ee048-374">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="ee048-375">Это трехмерные модели и соответствующих материалов, которые являются частью готовых сцены, вы будете работать.</span><span class="sxs-lookup"><span data-stu-id="ee048-375">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="ee048-376">В этом курсе вы напишете большая часть кода.</span><span class="sxs-lookup"><span data-stu-id="ee048-376">You will write the majority of the code in this course.</span></span>

    ![Импорт пакета MLProducts Unity](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="ee048-378">В рамках **панель проекта** папке, щелкните на **сцены** папку и дважды щелкните внутри сцены (вызывается **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="ee048-378">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="ee048-379">Сцены откроется (см. рисунок ниже).</span><span class="sxs-lookup"><span data-stu-id="ee048-379">The scene will open (see image below).</span></span> <span data-ttu-id="ee048-380">Если отсутствуют red бубны, просто щелкните **элементы** кнопку в верхней правой части **панели Game**.</span><span class="sxs-lookup"><span data-stu-id="ee048-380">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Импорт пакета MLProducts Unity](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="ee048-382">Глава 7 - Проверка библиотек DLL в Unity</span><span class="sxs-lookup"><span data-stu-id="ee048-382">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="ee048-383">Чтобы использовать библиотеки JSON (используется для сериализации и десериализации), с пакетом, который отображался в реализована Newtonsoft DLL.</span><span class="sxs-lookup"><span data-stu-id="ee048-383">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="ee048-384">Библиотека должна иметь правильные настройки, хотя следует (особенно если у вас возникают проблемы с кодом не работает).</span><span class="sxs-lookup"><span data-stu-id="ee048-384">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="ee048-385">Для этого сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="ee048-385">To do so:</span></span>

-  <span data-ttu-id="ee048-386">Щелкните левой кнопкой мыши на файле Newtonsoft внутри папки подключаемых модулей и просмотрите **панели Инспектора**.</span><span class="sxs-lookup"><span data-stu-id="ee048-386">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="ee048-387">Убедитесь, что **Any платформы** установлен.</span><span class="sxs-lookup"><span data-stu-id="ee048-387">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="ee048-388">Перейдите к **вкладке UWP** и также обеспечивают **не обрабатывать** установлен.</span><span class="sxs-lookup"><span data-stu-id="ee048-388">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Импорт библиотек DLL в Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="ee048-390">Глава 8 - создать класс ShelfKeeper</span><span class="sxs-lookup"><span data-stu-id="ee048-390">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="ee048-391">**ShelfKeeper** класс размещает методы, определяющие пользовательского интерфейса и продуктов, порожденных в сцене.</span><span class="sxs-lookup"><span data-stu-id="ee048-391">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="ee048-392">В рамках импортированного пакета будет у пользователя имеется этот класс на то, что он не полон.</span><span class="sxs-lookup"><span data-stu-id="ee048-392">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="ee048-393">Теперь пришло время для завершения этого класса:</span><span class="sxs-lookup"><span data-stu-id="ee048-393">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="ee048-394">Дважды щелкните **ShelfKeeper** сценарий, в **сценарии** , откройте папку с **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="ee048-394">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="ee048-395">Замените весь код, существующий в скрипте следующим кодом, которое задает дату и время и имеет метод для отображения продукта.</span><span class="sxs-lookup"><span data-stu-id="ee048-395">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

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

3.  <span data-ttu-id="ee048-396">Не забудьте сохранить изменения в **Visual Studio** перед возвратом **Unity**.</span><span class="sxs-lookup"><span data-stu-id="ee048-396">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="ee048-397">Обратно в редакторе Unity, убедитесь, что **ShelfKeeper** класс выглядит как ниже:</span><span class="sxs-lookup"><span data-stu-id="ee048-397">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Создание класса ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="ee048-399">Если скрипт не имеет целевых объектов по ссылке (т. е. *даты (текст Mesh)*), просто перетащите соответствующие объекты из **панели иерархии**, в целевой объект поля.</span><span class="sxs-lookup"><span data-stu-id="ee048-399">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="ee048-400">Ниже приведены сведения о работе, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="ee048-400">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="ee048-401">Откройте **точки Spawn** массива в **ShelfKeeper** компонента скрипта, щелкнув левой кнопкой мыши его.</span><span class="sxs-lookup"><span data-stu-id="ee048-401">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="ee048-402">Появится вызываемой подраздел **размер**, который указывает размер массива.</span><span class="sxs-lookup"><span data-stu-id="ee048-402">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="ee048-403">Тип **3** в текстовое поле рядом с полем **размер** и нажмите клавишу **ввод**, и три слота будет создан под.</span><span class="sxs-lookup"><span data-stu-id="ee048-403">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="ee048-404">В рамках **иерархии** разверните **отображения времени** объекта (с левой кнопкой мыши стрелку рядом с ним).</span><span class="sxs-lookup"><span data-stu-id="ee048-404">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="ee048-405">Далее щелкните ***Main Camera*** изнутри **иерархии**, так что **инспектор** его сведениями.</span><span class="sxs-lookup"><span data-stu-id="ee048-405">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="ee048-406">Выберите **главной камеры** в **панели иерархии**.</span><span class="sxs-lookup"><span data-stu-id="ee048-406">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="ee048-407">Перетащите **даты** и **время** объектов из **панели иерархии** для **текстовой даты** и **текста во время** Слоты в **инспектор** из **Main Camera** в **ShelfKeeper** компонента.</span><span class="sxs-lookup"><span data-stu-id="ee048-407">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="ee048-408">Перетащите **точки Spawn** из **панели иерархии** (под *полки* объект) для **3** **элемент**ссылаются на целевые объекты под **Spawn точки** массива, как показано на рисунке.</span><span class="sxs-lookup"><span data-stu-id="ee048-408">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Создание класса ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="ee048-410">Глава 9 — создать класс ProductPrediction</span><span class="sxs-lookup"><span data-stu-id="ee048-410">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="ee048-411">Далее нужно создать класс является **ProductPrediction** класса.</span><span class="sxs-lookup"><span data-stu-id="ee048-411">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="ee048-412">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="ee048-412">This class is responsible for:</span></span>

-   <span data-ttu-id="ee048-413">Запрос **службы машинного обучения** экземпляр, который предоставляет текущую дату и время.</span><span class="sxs-lookup"><span data-stu-id="ee048-413">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="ee048-414">Десериализации ответа JSON в полезных данных.</span><span class="sxs-lookup"><span data-stu-id="ee048-414">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="ee048-415">Интерпретации данных, получение 3 рекомендуемых продуктов.</span><span class="sxs-lookup"><span data-stu-id="ee048-415">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="ee048-416">Вызов **ShelfKeeper** методы для отображения данных в сцене класса.</span><span class="sxs-lookup"><span data-stu-id="ee048-416">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="ee048-417">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="ee048-417">To create this class:</span></span>

1.  <span data-ttu-id="ee048-418">Перейдите к **сценарии** папку в **панель проекта**.</span><span class="sxs-lookup"><span data-stu-id="ee048-418">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="ee048-419">Щелкните правой кнопкой мыши внутри папки **создать** > **C\# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="ee048-419">Right-click inside the folder, **Create** > **C\# Script**.</span></span> <span data-ttu-id="ee048-420">Вызовите сценарий **ProductPrediction**.</span><span class="sxs-lookup"><span data-stu-id="ee048-420">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="ee048-421">Дважды щелкните новый **ProductPrediction** скрипт, чтобы открыть его с **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="ee048-421">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="ee048-422">Если **обнаружено изменение файла** диалоговое окно появится, нажмите кнопку \***перезагрузить решение**.</span><span class="sxs-lookup"><span data-stu-id="ee048-422">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="ee048-423">Добавьте следующие пространства имен в начало класса ProductPrediction:</span><span class="sxs-lookup"><span data-stu-id="ee048-423">Add the following namespaces to the top of the ProductPrediction class:</span></span>

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

6.  <span data-ttu-id="ee048-424">Внутри **ProductPrediction** класса вставьте следующие два объекта, которые состоят из нескольких вложенных классов.</span><span class="sxs-lookup"><span data-stu-id="ee048-424">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="ee048-425">Эти классы используются для сериализации и десериализации JSON для службы машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="ee048-425">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

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

7.  <span data-ttu-id="ee048-426">Затем добавьте следующие переменные выше предыдущий код (таким образом, связанные с JSON, что код в нижней части сценария, кода, все остальные функции и выходом из способ):</span><span class="sxs-lookup"><span data-stu-id="ee048-426">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

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
    > <span data-ttu-id="ee048-427">Убедитесь, что для вставки **первичный ключ** и **конечную точку запрос ответ**, из портале машинного обучения, в переменные здесь.</span><span class="sxs-lookup"><span data-stu-id="ee048-427">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="ee048-428">Под изображениями Показать, где вам потребовалось бы ключ и конечную точку.</span><span class="sxs-lookup"><span data-stu-id="ee048-428">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Студия машинного обучения: Эксперимент](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="ee048-431">Вставьте этот код в **Start()** метод.</span><span class="sxs-lookup"><span data-stu-id="ee048-431">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="ee048-432">**Start()** метод вызывается при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="ee048-432">The **Start()** method is called when the class initializes:</span></span>

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

9.  <span data-ttu-id="ee048-433">Ниже приведен метод, который получает значение даты и времени из Windows и преобразует его в формат, который в нашем эксперименте машинного обучения можно использовать для сравнения с данными, хранящимися в таблице.</span><span class="sxs-lookup"><span data-stu-id="ee048-433">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

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

10. <span data-ttu-id="ee048-434">Вы можете **удалить** **Update()** метод, так как этот класс не будет его использовать.</span><span class="sxs-lookup"><span data-stu-id="ee048-434">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="ee048-435">Добавьте следующий метод, который будет взаимодействовать текущей даты и времени в конечной точке машинного обучения и получать ответ в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="ee048-435">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

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

12. <span data-ttu-id="ee048-436">Добавьте следующий метод, который отвечает за десериализацию ответ в формате JSON и обмен данными результат десериализации для **ShelfKeeper** класса.</span><span class="sxs-lookup"><span data-stu-id="ee048-436">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="ee048-437">Это приведет к появлению имена из трех элементов, согласно прогнозу продавать наиболее в текущую дату и время.</span><span class="sxs-lookup"><span data-stu-id="ee048-437">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="ee048-438">Вставьте приведенный ниже код в **ProductPrediction** класс, ниже предыдущего метода.</span><span class="sxs-lookup"><span data-stu-id="ee048-438">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

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

13. <span data-ttu-id="ee048-439">Сохранить **Visual Studio** и вернитесь к **Unity**.</span><span class="sxs-lookup"><span data-stu-id="ee048-439">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="ee048-440">Перетащите **ProductPrediction** класса скрипт из **сценарий** папку, на **Main Camera** объекта.</span><span class="sxs-lookup"><span data-stu-id="ee048-440">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="ee048-441">Сохраните сцену и проект **файл** > ***сохранить сцену* / *файл***   >  **Сохранить проект**.</span><span class="sxs-lookup"><span data-stu-id="ee048-441">Save your scene and project **File** > ***Save Scene* / *File*** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="ee048-442">Глава 10 - выполнить сборку решения универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="ee048-442">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="ee048-443">Пришло время выполнить сборку проекта в качестве решения UWP может выполняться как отдельное приложение.</span><span class="sxs-lookup"><span data-stu-id="ee048-443">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="ee048-444">Для сборки:</span><span class="sxs-lookup"><span data-stu-id="ee048-444">To Build:</span></span>

1.  <span data-ttu-id="ee048-445">Сохранить текущую сцену, щелкнув **файл** **сохранить сцены**.</span><span class="sxs-lookup"><span data-stu-id="ee048-445">Save the current scene by clicking on **File** **Save Scenes**.</span></span>

2.  <span data-ttu-id="ee048-446">Перейдите к **файл** **параметры сборки**</span><span class="sxs-lookup"><span data-stu-id="ee048-446">Go to **File** **Build Settings**</span></span>

3.  <span data-ttu-id="ee048-447">Проверьте поле, называемое **Unity C\# проекты** (это важно, так как он позволит вам изменить классы, после завершения сборки).</span><span class="sxs-lookup"><span data-stu-id="ee048-447">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="ee048-448">Щелкните **Добавление открытых сцен**,</span><span class="sxs-lookup"><span data-stu-id="ee048-448">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="ee048-449">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="ee048-449">Click **Build**.</span></span>

    ![Выполните сборку решения универсальной платформы Windows](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="ee048-451">Вам будет предложено выбрать папку, где требуется выполнить сборку решения.</span><span class="sxs-lookup"><span data-stu-id="ee048-451">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="ee048-452">Создание **ПОСТРОЕНИЯ** папку и в этой папке создайте другую папку с соответствующим именем, по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="ee048-452">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="ee048-453">Щелкните новую папку и нажмите кнопку **Выбор папки**, чтобы начать построение в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="ee048-453">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Выполните сборку решения универсальной платформы Windows](images/AzureLabs-Lab7-55.png)

    ![Выполните сборку решения универсальной платформы Windows](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="ee048-456">Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).</span><span class="sxs-lookup"><span data-stu-id="ee048-456">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="ee048-457">Глава 11 - развертывания приложения</span><span class="sxs-lookup"><span data-stu-id="ee048-457">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="ee048-458">Для развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="ee048-458">To deploy your application:</span></span>

1.  <span data-ttu-id="ee048-459">Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ee048-459">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="ee048-460">Откройте Visual Studio вам потребуется восстановить пакеты NuGet, который можно сделать с помощью щелкнув MachineLearningLab_Build решения, в обозревателе решений (находится справа от Visual Studio) щелкните правой кнопкой мыши и выбрав восстановить пакеты NuGet.</span><span class="sxs-lookup"><span data-stu-id="ee048-460">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Добавьте пакеты NuGet](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="ee048-462">В списке выберите конфигурацию решения **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="ee048-462">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="ee048-463">В платформу решения, выберите **x86**, **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="ee048-463">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="ee048-464">Для Microsoft HoloLens, может быть проще устанавливать равным *удаленный компьютер*, таким образом, не связанном устройстве на компьютер.</span><span class="sxs-lookup"><span data-stu-id="ee048-464">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="ee048-465">Однако необходимо будет выполнить следующее:</span><span class="sxs-lookup"><span data-stu-id="ee048-465">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="ee048-466">Знать **IP-адрес** из HoloLens, которую можно найти в *параметры > сеть и Интернет > Wi-Fi > Дополнительно*; IPv4 — это адрес, следует использовать.</span><span class="sxs-lookup"><span data-stu-id="ee048-466">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="ee048-467">Убедитесь, **режим разработчика** — **на**; найдено в *параметры > обновление и безопасность > для разработчиков*.</span><span class="sxs-lookup"><span data-stu-id="ee048-467">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Добавьте пакеты NuGet](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="ee048-469">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на вашем ПК.</span><span class="sxs-lookup"><span data-stu-id="ee048-469">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="ee048-470">Приложения появятся в списке установленных приложений, Готово к запуску.</span><span class="sxs-lookup"><span data-stu-id="ee048-470">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="ee048-471">При запуске приложения смешанной реальности, вы увидите bench, которая была создана в сцене Unity, и от инициализации, будут выбираться данные, которые можно настроить в Azure.</span><span class="sxs-lookup"><span data-stu-id="ee048-471">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="ee048-472">Данные, которые будут десериализованы в вашем приложении, и три лучших результатов для текущей датой и временем будет предоставляться визуально три модели на bench.</span><span class="sxs-lookup"><span data-stu-id="ee048-472">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="ee048-473">Готового приложения машинного обучения</span><span class="sxs-lookup"><span data-stu-id="ee048-473">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="ee048-474">Поздравляем, вы создали приложение смешанной реальности, которое использует машинное обучение Azure для прогнозирования данных и их отображения на сцены.</span><span class="sxs-lookup"><span data-stu-id="ee048-474">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Добавьте пакеты NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="ee048-476">Упражнение</span><span class="sxs-lookup"><span data-stu-id="ee048-476">Exercise</span></span>

<span data-ttu-id="ee048-477">**Упражнение 1**</span><span class="sxs-lookup"><span data-stu-id="ee048-477">**Exercise 1**</span></span>

<span data-ttu-id="ee048-478">Поэкспериментируйте с порядком сортировки, приложения и имеют три нижних прогнозы отображаются на полки, как эти данные потенциально полезным также.</span><span class="sxs-lookup"><span data-stu-id="ee048-478">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="ee048-479">**Упражнение 2**</span><span class="sxs-lookup"><span data-stu-id="ee048-479">**Exercise 2**</span></span>

<span data-ttu-id="ee048-480">С помощью **таблицы Azure** Заполните новую таблицу с информацией о погоде и создайте новый эксперимент, используя данные.</span><span class="sxs-lookup"><span data-stu-id="ee048-480">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
