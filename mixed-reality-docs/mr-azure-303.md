---
title: Г-н и 303 Azure - естественного языка, основные сведения о (LUIS)
description: Выполните этот курс, чтобы узнать, как реализовать приложение смешанной реальности Azure Language Understanding Intelligence Service (LUIS).
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, интеллектуальная служба анализа языка, luis, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603072"
---
>[!NOTE]
><span data-ttu-id="88089-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="88089-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="88089-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="88089-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="88089-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="88089-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="88089-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="88089-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="88089-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="88089-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="88089-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="88089-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="88089-110">Г-н и Azure 303: Понимание естественного языка (LUIS)</span><span class="sxs-lookup"><span data-stu-id="88089-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="88089-111">В рамках этого курса вы узнаете, как интегрировать в приложение смешанной реальности, с помощью Azure Cognitive Services, с помощью API понимания языка Language Understanding.</span><span class="sxs-lookup"><span data-stu-id="88089-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![Результат лаборатории](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="88089-113">*Language Understanding (LUIS)* — это служба Microsoft Azure, которую предоставляет приложениям возможность вносить значения из введенных данных, например, посредством извлечения, что пользователь может возникнуть, по их собственным словам.</span><span class="sxs-lookup"><span data-stu-id="88089-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="88089-114">Это достигается с помощью машинного обучения, которое распознает и изучает входные данные, а затем можно ответить с помощью соответствующих, подробную информацию.</span><span class="sxs-lookup"><span data-stu-id="88089-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="88089-115">Дополнительные сведения см. в статье [страницы Azure Language Understanding (LUIS)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="88089-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="88089-116">После выполнения этого курса, у вас будет приложение иммерсивных гарнитуры смешанной реальности, которое сможет выполнить следующие:</span><span class="sxs-lookup"><span data-stu-id="88089-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="88089-117">Запись речи ввода пользователя, с помощью микрофона, подключенного к иммерсивных гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="88089-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="88089-118">Отправьте записанный диктовки *Azure Language Understanding Intelligent Service* (*LUIS*).</span><span class="sxs-lookup"><span data-stu-id="88089-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="88089-119">Иметь LUIS извлечения, то есть от отправки сведений, который будет анализироваться и пытаться определить цели запроса пользователя будут внесены.</span><span class="sxs-lookup"><span data-stu-id="88089-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="88089-120">Разработки будет включать создание приложения, где пользователь сможет использовать голосовые и/или помощи, чтобы изменить размер и цвет объекты на сцене.</span><span class="sxs-lookup"><span data-stu-id="88089-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="88089-121">Использование контроллеров движения здесь не рассматриваются.</span><span class="sxs-lookup"><span data-stu-id="88089-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="88089-122">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="88089-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="88089-123">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="88089-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="88089-124">Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="88089-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="88089-125">Приготовьтесь Train LUIS несколько раз, который рассматривается в [Глава 12](#chapter-12--improving-your-luis-service).</span><span class="sxs-lookup"><span data-stu-id="88089-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="88089-126">Дополнительные случаи, когда будет обучена LUIS позволит добиться лучших результатов.</span><span class="sxs-lookup"><span data-stu-id="88089-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="88089-127">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="88089-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="88089-128">Курс</span><span class="sxs-lookup"><span data-stu-id="88089-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="88089-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="88089-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="88089-130"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="88089-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="88089-131">Г-н и Azure 303: Понимание естественного языка (LUIS)</span><span class="sxs-lookup"><span data-stu-id="88089-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="88089-132">✔️</span><span class="sxs-lookup"><span data-stu-id="88089-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="88089-133">✔️</span><span class="sxs-lookup"><span data-stu-id="88089-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="88089-134">Хотя этот курс основное внимание уделяется Windows Mixed Reality иммерсивную (VR), можно также применить полученные знания в этом курсе для Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88089-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="88089-135">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="88089-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="88089-136">При использовании HoloLens, вы можете заметить некоторые echo во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="88089-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88089-137">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="88089-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="88089-138">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="88089-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="88089-139">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="88089-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="88089-140">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .</span><span class="sxs-lookup"><span data-stu-id="88089-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="88089-141">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="88089-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="88089-142">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="88089-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="88089-143">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="88089-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="88089-144">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="88089-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="88089-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="88089-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="88089-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="88089-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="88089-147">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="88089-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="88089-148">Наушники с помощью встроенного микрофона (если гарнитура отсутствует встроенный mic, а также докладчиков)</span><span class="sxs-lookup"><span data-stu-id="88089-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="88089-149">Доступ к Интернету для настройки Azure и извлечения LUIS</span><span class="sxs-lookup"><span data-stu-id="88089-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="88089-150">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="88089-150">Before you start</span></span>

1.  <span data-ttu-id="88089-151">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="88089-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="88089-152">Чтобы разрешить компьютер, чтобы включить режим диктовки, перейдите к **параметры Windows > конфиденциальности > речи, рукописного ввода и введя** и нажмите кнопку **Включение службы распознавания речи и ввода предложения**.</span><span class="sxs-lookup"><span data-stu-id="88089-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="88089-153">Код в этом руководстве, позволит вам требуется записать **микрофон устройством по умолчанию** на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="88089-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="88089-154">Убедитесь, что устройства "микрофон" по умолчанию имеет значение, которое вы хотите использовать для записи голоса.</span><span class="sxs-lookup"><span data-stu-id="88089-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="88089-155">Если ваш гарнитура имеет встроенный микрофон, убедитесь, что параметр *«После я wear Мой гарнитуры, перейдите на mic гарнитура»* включен *смешанной реальности портала* параметры.</span><span class="sxs-lookup"><span data-stu-id="88089-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Настройка иммерсивных гарнитура](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="88089-157">Глава 1 – Настройка портала Azure</span><span class="sxs-lookup"><span data-stu-id="88089-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="88089-158">Чтобы использовать *Language Understanding* службы в Azure, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="88089-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="88089-159">Войдите в [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="88089-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="88089-160">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="88089-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="88089-161">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="88089-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="88089-162">После входа в систему щелкните **New** в левом верхнем углу, а поиск *Language Understanding*и нажмите кнопку **ввод**.</span><span class="sxs-lookup"><span data-stu-id="88089-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![Создание ресурса LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="88089-164">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="88089-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="88089-165">Новая страница справа будет предоставить описание службы Language Understanding.</span><span class="sxs-lookup"><span data-stu-id="88089-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="88089-166">В нижней левой части этой страницы выберите **создать** кнопку, чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="88089-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Создание службы LUIS - Юридическая информация](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="88089-168">После нажатия на создание:</span><span class="sxs-lookup"><span data-stu-id="88089-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="88089-169">Вставить нужный **имя** для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="88089-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="88089-170">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="88089-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="88089-171">Выберите **Ценовая** подходит для вас, если это первое времени на создание *службы LUIS*, уровень "бесплатный" (с именем F0) должны быть доступны для вас.</span><span class="sxs-lookup"><span data-stu-id="88089-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="88089-172">Бесплатный выделение должно быть более чем достаточно для этого курса.</span><span class="sxs-lookup"><span data-stu-id="88089-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="88089-173">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="88089-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="88089-174">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="88089-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="88089-175">Рекомендуется хранить все службы Azure, связанные с один проект (например, такие как этих курсов) для распространенных группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="88089-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="88089-176">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="88089-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="88089-177">Определить **расположение** для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="88089-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="88089-178">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="88089-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="88089-179">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="88089-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="88089-180">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="88089-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="88089-181">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="88089-181">Select **Create**.</span></span>

        ![Создание службы LUIS — ввод данных пользователем](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="88089-183">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="88089-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="88089-184">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="88089-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Новый образ уведомлений Azure](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="88089-186">Щелкните уведомление, чтобы изучить ваш новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="88089-186">Click on the notification to explore your new Service instance.</span></span>

    ![Уведомление о создании успешно ресурсов](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="88089-188">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="88089-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="88089-189">Откроется в новом экземпляре службы LUIS.</span><span class="sxs-lookup"><span data-stu-id="88089-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![Доступ к ключам LUIS](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="88089-191">В этом руководстве описано приложение должно выполнять вызовы в службу, которая осуществляется с помощью ключа подписки вашей службы.</span><span class="sxs-lookup"><span data-stu-id="88089-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="88089-192">Из *быстрого запуска* странице из вашей *LUIS API* службы, перейдите к первому шагу *получите ключи*и нажмите кнопку **ключи** (вы также можете добиться этого, щелкнув синий гиперссылки ключи, расположенный в меню навигации служб, обозначенное с помощью значок ключа).</span><span class="sxs-lookup"><span data-stu-id="88089-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="88089-193">Это позволит службе *ключи*.</span><span class="sxs-lookup"><span data-stu-id="88089-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="88089-194">Сделайте копию один из отображаемых разделов, так как он потребуется позже в проекте.</span><span class="sxs-lookup"><span data-stu-id="88089-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="88089-195">В *службы* нажмите кнопку *портал Language Understanding* перенаправление на веб-страницу, который будет использоваться для создания новой службы, в приложении LUIS.</span><span class="sxs-lookup"><span data-stu-id="88089-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="88089-196">Глава 2 – на портал Language Understanding</span><span class="sxs-lookup"><span data-stu-id="88089-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="88089-197">В этом разделе вы узнаете, как сделать приложения LUIS на портале LUIS.</span><span class="sxs-lookup"><span data-stu-id="88089-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="88089-198">Имейте в виду, что настройка *сущностей*, *намерения*, и *фразы* в этой главе является только первым шагом при создании вашей службы LUIS: также необходимо будет переобучить службу, несколько раз, поэтому для обеспечивают более высокую точность.</span><span class="sxs-lookup"><span data-stu-id="88089-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="88089-199">Повторное обучение службы рассматривается в [последняя глава](#chapter-12--improving-your-luis-service) этого курса, поэтому убедитесь, завершить его.</span><span class="sxs-lookup"><span data-stu-id="88089-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="88089-200">При достижении *портал Language Understanding*, может потребоваться войти в систему, если вы еще не сделали, с теми же учетными данными, как портал Azure.</span><span class="sxs-lookup"><span data-stu-id="88089-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![Страница входа LUIS](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="88089-202">Это при первом использовании LUIS, необходимо будет выполнить прокрутку вниз до нижней части начальной страницы, найдите и щелкните **приложения создайте LUIS** кнопки.</span><span class="sxs-lookup"><span data-stu-id="88089-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![Создание страницы приложения LUIS](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="88089-204">После входа в систему, щелкните **Мои приложения** (Если вы не в этом разделе в данный момент).</span><span class="sxs-lookup"><span data-stu-id="88089-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="88089-205">Вы можете нажать на **создать приложение**.</span><span class="sxs-lookup"><span data-stu-id="88089-205">You can then click on **Create new app**.</span></span>

    ![ЛУИС - образ приложения](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="88089-207">Присвойте приложению *имя*.</span><span class="sxs-lookup"><span data-stu-id="88089-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="88089-208">Если приложения должны понимать языке, отличном от английского, следует изменить *языка и региональных параметров* для соответствующего языка.</span><span class="sxs-lookup"><span data-stu-id="88089-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="88089-209">Здесь вы можете также добавить *описание* для нового приложения LUIS.</span><span class="sxs-lookup"><span data-stu-id="88089-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![ЛУИС - Создание нового приложения](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="88089-211">После нажатия кнопки **сделать**, необходимо ввести *построения* новой странице *LUIS* приложения.</span><span class="sxs-lookup"><span data-stu-id="88089-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="88089-212">Существует несколько важных понятий здесь:</span><span class="sxs-lookup"><span data-stu-id="88089-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="88089-213">*Намерение*, представляющий метод, который будет вызываться после запроса от пользователя.</span><span class="sxs-lookup"><span data-stu-id="88089-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="88089-214">*НАМЕРЕНИЕ* может иметь один или несколько *СУЩНОСТЕЙ*.</span><span class="sxs-lookup"><span data-stu-id="88089-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="88089-215">*Сущность*, входит в состав запроса, который описывает сведения, относящиеся к *НАМЕРЕНИЕ*.</span><span class="sxs-lookup"><span data-stu-id="88089-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="88089-216">*Фразы продолжительностью*, предоставляются примеры запросов разработчиком, LUIS, будет использовать для подготовки.</span><span class="sxs-lookup"><span data-stu-id="88089-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="88089-217">Если эти понятия не вполне снимите, не волнуйтесь, так как этот курс прояснить их далее в этой главе.</span><span class="sxs-lookup"><span data-stu-id="88089-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="88089-218">Сначала путем создания *сущностей* необходимые для создания этого курса.</span><span class="sxs-lookup"><span data-stu-id="88089-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="88089-219">В левой части страницы щелкните *сущностей*, затем щелкните **создать новую сущность**.</span><span class="sxs-lookup"><span data-stu-id="88089-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Создание новой сущности](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="88089-221">Вызовите новую сущность *цвет*, установите для него *простой*, нажмите клавишу **сделать**.</span><span class="sxs-lookup"><span data-stu-id="88089-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Создание простого объекта - цвет](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="88089-223">Повторите эту процедуру для создания трех (3) Дополнительные простые сущности с именем:</span><span class="sxs-lookup"><span data-stu-id="88089-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="88089-224">*преобразования*</span><span class="sxs-lookup"><span data-stu-id="88089-224">*upsize*</span></span>
    -   <span data-ttu-id="88089-225">*уменьшить*</span><span class="sxs-lookup"><span data-stu-id="88089-225">*downsize*</span></span>
    -   <span data-ttu-id="88089-226">*target*</span><span class="sxs-lookup"><span data-stu-id="88089-226">*target*</span></span>

<span data-ttu-id="88089-227">Результат должен выглядеть как на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="88089-227">The result should look like the image below:</span></span>

![Результат создания сущности](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="88089-229">На этом этапе можно начать создавать *Intents*.</span><span class="sxs-lookup"><span data-stu-id="88089-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="88089-230">Не удаляйте **None** намерение.</span><span class="sxs-lookup"><span data-stu-id="88089-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="88089-231">В левой части страницы щелкните **Intents**, затем щелкните **создать новый намерение**.</span><span class="sxs-lookup"><span data-stu-id="88089-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Создание новых инструментов intents](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="88089-233">Вызовите новый *намерение* **ChangeObjectColor**.</span><span class="sxs-lookup"><span data-stu-id="88089-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="88089-234">Это *намерение* имя используется внутри кода далее в этом курсе, поэтому для получения наилучших результатов используйте это имя предоставленное.</span><span class="sxs-lookup"><span data-stu-id="88089-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="88089-235">После того как вы убедились, имя, которое вы будете перенаправлены на страницу намерения.</span><span class="sxs-lookup"><span data-stu-id="88089-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![ЛУИС - намерения страницы](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="88089-237">Вы заметите, что есть текстовое поле, запрашивающее типу, 5 или более разных *фразы*.</span><span class="sxs-lookup"><span data-stu-id="88089-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="88089-238">LUIS преобразует все фразы в нижний регистр.</span><span class="sxs-lookup"><span data-stu-id="88089-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="88089-239">Вставьте следующий текст *Utterance* в верхнем поле (в настоящее время с текстом *тип около 5 примеры...*</span><span class="sxs-lookup"><span data-stu-id="88089-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="88089-240">) и нажмите клавишу **ввод**:</span><span class="sxs-lookup"><span data-stu-id="88089-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="88089-241">Можно будет заметить, что новый *Utterance* отобразится в списке ниже.</span><span class="sxs-lookup"><span data-stu-id="88089-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="88089-242">После выполнения вставьте следующие фразы шести (6):</span><span class="sxs-lookup"><span data-stu-id="88089-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="88089-243">Для каждого Utterance, которую вы создали необходимо определить, какие слова должна использоваться LUIS как сущности.</span><span class="sxs-lookup"><span data-stu-id="88089-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="88089-244">В этом примере необходимо пометить все цвета как *цвет* сущности и всех возможных ссылку на объект как *целевой* сущности.</span><span class="sxs-lookup"><span data-stu-id="88089-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="88089-245">Чтобы сделать это, попробуйте щелкнуть слово *цилиндра* в первый Utterance и выберите *целевой*.</span><span class="sxs-lookup"><span data-stu-id="88089-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Определение целевых объектов Utterance](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="88089-247">Теперь щелкните слово *red* в первый Utterance и выберите *цвет*.</span><span class="sxs-lookup"><span data-stu-id="88089-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Идентификация сущностей Utterance](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="88089-249">Метка следующей строке, кроме того, где *куба* должно быть *целевой*, и *черной* должно быть *цвет*.</span><span class="sxs-lookup"><span data-stu-id="88089-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="88089-250">Обратите также внимание на использование слов *«this»*, *«it»*, и *«этот объект»*, которой предоставляются, так что иметь отслеживании целевой типы доступных также.</span><span class="sxs-lookup"><span data-stu-id="88089-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="88089-251">Повторите описанный выше процесс, все фразы иметь сущности меткой.</span><span class="sxs-lookup"><span data-stu-id="88089-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="88089-252">См. в разделе под изображением, если вам нужна помощь.</span><span class="sxs-lookup"><span data-stu-id="88089-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="88089-253">При выборе слов, которые они помечены как сущности:</span><span class="sxs-lookup"><span data-stu-id="88089-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="88089-254">Для отдельных слов просто щелкните их.</span><span class="sxs-lookup"><span data-stu-id="88089-254">For single words just click them.</span></span>
    > - <span data-ttu-id="88089-255">В наборе два или несколько слов щелкните в начале, а затем в конце набора.</span><span class="sxs-lookup"><span data-stu-id="88089-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="88089-256">Можно использовать *представление маркеры* кнопки-переключателя для переключения между **сущностей или просмотре маркеры**!</span><span class="sxs-lookup"><span data-stu-id="88089-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="88089-257">Результаты должны быть, как показано на рисунке ниже, отображение **сущностей или просмотре маркеры**:</span><span class="sxs-lookup"><span data-stu-id="88089-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Маркеры & представлений сущностей](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="88089-259">После этого нажмите клавишу **Train** кнопку в правой верхней части страницы и дождитесь небольшой индикатор round ее, чтобы стать зеленым.</span><span class="sxs-lookup"><span data-stu-id="88089-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="88089-260">Это означает, что LUIS успешного обучения распознавать этой цели.</span><span class="sxs-lookup"><span data-stu-id="88089-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![Обучение LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="88089-262">В качестве упражнения для вас создать новый намерения с именем **ChangeObjectSize**, в которых используются сущности *целевой*, *преобразования*, и *уменьшать их размер*.</span><span class="sxs-lookup"><span data-stu-id="88089-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="88089-263">Следуя тому же процессу, как предыдущим намерением, вставьте следующие фразы 8 (восьми) для *размер* изменить:</span><span class="sxs-lookup"><span data-stu-id="88089-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="88089-264">Результат должен быть, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="88089-264">The result should be like the one in the image below:</span></span>

    ![Настройка маркеров ChangeObjectSize / сущностей](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="88089-266">Один раз обоих намерения **ChangeObjectColor** и **ChangeObjectSize**, будут созданы и обучения, щелкните **публикации** кнопку в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="88089-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![Публикация службы LUIS](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="88089-268">На *публикации* страниц будет финализировать и публикация приложения LUIS, таким образом, чтобы он доступен в коде.</span><span class="sxs-lookup"><span data-stu-id="88089-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="88089-269">Отставить раскрывающегося *публиковать в* как **рабочей**.</span><span class="sxs-lookup"><span data-stu-id="88089-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="88089-270">Задайте *часовой пояс* в местный часовой пояс.</span><span class="sxs-lookup"><span data-stu-id="88089-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="88089-271">Установите флажок **Include все прогнозируемые оценки намерения**.</span><span class="sxs-lookup"><span data-stu-id="88089-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="88089-272">Щелкните **опубликовать рабочий слот**.</span><span class="sxs-lookup"><span data-stu-id="88089-272">Click on **Publish to Production Slot**.</span></span>

        ![Параметры публикации](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="88089-274">В разделе *ресурсы и ключи*:</span><span class="sxs-lookup"><span data-stu-id="88089-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="88089-275">Выберите регион, установленные для экземпляра службы на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="88089-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="88089-276">Обратите внимание, **Starter_Key** элемент ниже, игнорируйте его.</span><span class="sxs-lookup"><span data-stu-id="88089-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="88089-277">Щелкните **добавить ключ** и вставить *ключ* , полученный на портале Azure при создании своего экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="88089-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="88089-278">В тот же пользователь, вошедший в Azure и портала LUIS, вам будут предоставлены раскрывающиеся меню для *имя_клиента*, *Имя_подписки*и *ключ* вы хотите использовать () как было введено ранее на портале Azure будет тем же именем.</span><span class="sxs-lookup"><span data-stu-id="88089-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="88089-279">Под *конечной точки*, сделайте копию конечной точки, соответствующее ключу вставки, вскоре он будет использоваться в коде.</span><span class="sxs-lookup"><span data-stu-id="88089-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="88089-280">Глава 3 – Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="88089-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="88089-281">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="88089-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="88089-282">Откройте *Unity* и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="88089-282">Open *Unity* and click **New**.</span></span> 

    ![Начните новый проект Unity.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="88089-284">Введите имя проекта Unity, теперь нужно вставить **MR_LUIS**.</span><span class="sxs-lookup"><span data-stu-id="88089-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="88089-285">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="88089-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="88089-286">Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="88089-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="88089-287">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="88089-287">Then, click **Create project**.</span></span>

    ![Укажите сведения для нового проекта Unity.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="88089-289">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="88089-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="88089-290">Откройте для редактирования > Параметры и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="88089-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="88089-291">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="88089-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="88089-292">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="88089-292">Close the **Preferences** window.</span></span>

    ![Обновите настройки редактора скриптов.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="88089-294">Перейдите к **файл > Параметры сборки** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **переключения платформы** кнопки.</span><span class="sxs-lookup"><span data-stu-id="88089-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Создавайте окно "Параметры", переключить платформу для универсальной платформы Windows.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="88089-296">Перейдите к **файл > Параметры сборки** и убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="88089-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="88089-297">**Целевое устройство** присваивается **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="88089-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="88089-298">Microsoft HoloLens, задайте **целевое устройство** для *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="88089-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="88089-299">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="88089-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="88089-300">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="88089-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="88089-301">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="88089-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="88089-302">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="88089-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="88089-303">Сохраните сцены и добавить его к сборке.</span><span class="sxs-lookup"><span data-stu-id="88089-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="88089-304">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="88089-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="88089-305">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="88089-305">A save window will appear.</span></span>
        
            ![Нажмите кнопку Добавить кнопку open сцены](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="88089-307">Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="88089-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создание новой папки scripts](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="88089-309">Откройте только что созданный **сцены** папку, а затем в *имя файла*: текстовое поле, тип **MR_LuisScene**, нажмите клавишу **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="88089-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Присвойте имя новой сцены.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="88089-311">Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="88089-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="88089-312">В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится.</span><span class="sxs-lookup"><span data-stu-id="88089-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Открытие параметров проигрывателя.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="88089-314">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="88089-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="88089-315">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="88089-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="88089-316">**Версия среды выполнения сценариев** должно быть **стабильной** (.NET 3.5 эквивалент).</span><span class="sxs-lookup"><span data-stu-id="88089-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="88089-317">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="88089-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="88089-318">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="88089-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Обновите другие параметры.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="88089-320">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="88089-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="88089-321">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="88089-321">**InternetClient**</span></span>
        2. <span data-ttu-id="88089-322">**"Микрофон"**</span><span class="sxs-lookup"><span data-stu-id="88089-322">**Microphone**</span></span>

            ![Обновление параметров публикации.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="88089-324">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.</span><span class="sxs-lookup"><span data-stu-id="88089-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Обновление параметров R X.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="88089-326">Вернитесь в *параметры построения* _Unity C#_  проектов больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="88089-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="88089-327">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="88089-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="88089-328">Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="88089-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="88089-329">Глава 4 – Create сцены</span><span class="sxs-lookup"><span data-stu-id="88089-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88089-330">Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), импортировать его в проект в качестве [пользовательского пакета ](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 5](#chapter-5--create-the-microphonemanager-class).</span><span class="sxs-lookup"><span data-stu-id="88089-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="88089-331">Щелкните правой кнопкой мыши пустую часть области *панели иерархии*в разделе **трехмерный объект**, добавьте **плоскости**.</span><span class="sxs-lookup"><span data-stu-id="88089-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Создайте плоскость.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="88089-333">Имейте в виду, если щелкнуть правой кнопкой в *иерархии* еще раз, чтобы создать дополнительные объекты, если у вас есть последнего выделенного объекта, выбранного объекта должен стать родительским нового объекта.</span><span class="sxs-lookup"><span data-stu-id="88089-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="88089-334">Избегайте этого, щелчок левой кнопкой мыши в пустое место в иерархии, а затем щелкните правой кнопкой мыши.</span><span class="sxs-lookup"><span data-stu-id="88089-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="88089-335">Повторите описанные выше действия, чтобы добавить следующие объекты:</span><span class="sxs-lookup"><span data-stu-id="88089-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="88089-336">*Sphere*</span><span class="sxs-lookup"><span data-stu-id="88089-336">*Sphere*</span></span>
    2. <span data-ttu-id="88089-337">*Цилиндр*</span><span class="sxs-lookup"><span data-stu-id="88089-337">*Cylinder*</span></span>
    3. <span data-ttu-id="88089-338">*Куб*</span><span class="sxs-lookup"><span data-stu-id="88089-338">*Cube*</span></span>
    4. <span data-ttu-id="88089-339">*Трехмерный текст*</span><span class="sxs-lookup"><span data-stu-id="88089-339">*3D Text*</span></span>

4.  <span data-ttu-id="88089-340">Итоговый сцены *иерархии* должно быть, как показано на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="88089-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Настройка иерархии сцены.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="88089-342">Щелчок левой кнопкой на **Main Camera** для его выбора, рассмотрим *панели Инспектора* вы увидите объекта Camera со всеми его компонентов.</span><span class="sxs-lookup"><span data-stu-id="88089-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="88089-343">Щелкните **добавить компонент** расположенную в нижней части *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="88089-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Добавление аудио источника](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="88089-345">Поиск компонента, который называется *источника аудио*, как показано выше.</span><span class="sxs-lookup"><span data-stu-id="88089-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="88089-346">Также убедитесь, что *преобразования* компонент Main Camera присвоено (0,0,0), это можно сделать, нажав клавишу **шестеренки** значок рядом с камеры *преобразования* компонента и выбрав **сбросить**.</span><span class="sxs-lookup"><span data-stu-id="88089-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="88089-347">*Преобразования* компонент должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="88089-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="88089-348">*Позиция* присваивается **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="88089-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="88089-349">*Поворот* присваивается **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="88089-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="88089-350">Для Microsoft HoloLens, необходимо также изменить следующим образом, являются частью **камеры** компонент, который находится на вашей **Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="88089-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="88089-351">**Очистите флаги:** Сплошным цветом.</span><span class="sxs-lookup"><span data-stu-id="88089-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="88089-352">**Фон** "черная, альфа-канал 0" — Hex цвет: #00000000.</span><span class="sxs-lookup"><span data-stu-id="88089-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="88089-353">Щелчок левой кнопкой на **плоскости** чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="88089-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="88089-354">В *панели Инспектора* задать *преобразования* компонент со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="88089-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="88089-355">Преобразование - *позиции*</span><span class="sxs-lookup"><span data-stu-id="88089-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="88089-356">**X**</span><span class="sxs-lookup"><span data-stu-id="88089-356">**X**</span></span> | <span data-ttu-id="88089-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="88089-357">**Y**</span></span>                  | <span data-ttu-id="88089-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="88089-358">**Z**</span></span> |
    | <span data-ttu-id="88089-359">0</span><span class="sxs-lookup"><span data-stu-id="88089-359">0</span></span>     | <span data-ttu-id="88089-360">-1</span><span class="sxs-lookup"><span data-stu-id="88089-360">-1</span></span>                     | <span data-ttu-id="88089-361">0</span><span class="sxs-lookup"><span data-stu-id="88089-361">0</span></span>     |


10. <span data-ttu-id="88089-362">Щелчок левой кнопкой на **Sphere** чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="88089-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="88089-363">В *панели Инспектора* задать *преобразования* компонент со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="88089-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="88089-364">Преобразование - *позиции*</span><span class="sxs-lookup"><span data-stu-id="88089-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="88089-365">**X**</span><span class="sxs-lookup"><span data-stu-id="88089-365">**X**</span></span> | <span data-ttu-id="88089-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="88089-366">**Y**</span></span>                  | <span data-ttu-id="88089-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="88089-367">**Z**</span></span> |
    | <span data-ttu-id="88089-368">2</span><span class="sxs-lookup"><span data-stu-id="88089-368">2</span></span>     | <span data-ttu-id="88089-369">1</span><span class="sxs-lookup"><span data-stu-id="88089-369">1</span></span>                      | <span data-ttu-id="88089-370">2</span><span class="sxs-lookup"><span data-stu-id="88089-370">2</span></span>     |

11. <span data-ttu-id="88089-371">Щелчок левой кнопкой на **цилиндра** чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="88089-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="88089-372">В *панели Инспектора* задать *преобразования* компонент со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="88089-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="88089-373">Преобразование - *позиции*</span><span class="sxs-lookup"><span data-stu-id="88089-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="88089-374">**X**</span><span class="sxs-lookup"><span data-stu-id="88089-374">**X**</span></span> | <span data-ttu-id="88089-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="88089-375">**Y**</span></span>                  | <span data-ttu-id="88089-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="88089-376">**Z**</span></span> |
    | <span data-ttu-id="88089-377">-2</span><span class="sxs-lookup"><span data-stu-id="88089-377">-2</span></span>    | <span data-ttu-id="88089-378">1</span><span class="sxs-lookup"><span data-stu-id="88089-378">1</span></span>                      | <span data-ttu-id="88089-379">2</span><span class="sxs-lookup"><span data-stu-id="88089-379">2</span></span>     |

12. <span data-ttu-id="88089-380">Щелчок левой кнопкой на **куба** чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="88089-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="88089-381">В *панели Инспектора* задать *преобразования* компонент со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="88089-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="88089-382">Преобразование - *позиции*</span><span class="sxs-lookup"><span data-stu-id="88089-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="88089-383">Преобразование - *поворота*</span><span class="sxs-lookup"><span data-stu-id="88089-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="88089-384">**X**</span><span class="sxs-lookup"><span data-stu-id="88089-384">**X**</span></span> | <span data-ttu-id="88089-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="88089-385">**Y**</span></span>                   | <span data-ttu-id="88089-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="88089-386">**Z**</span></span> |  \| | <span data-ttu-id="88089-387">**X**</span><span class="sxs-lookup"><span data-stu-id="88089-387">**X**</span></span> | <span data-ttu-id="88089-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="88089-388">**Y**</span></span>                  | <span data-ttu-id="88089-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="88089-389">**Z**</span></span> |
    | <span data-ttu-id="88089-390">0</span><span class="sxs-lookup"><span data-stu-id="88089-390">0</span></span>     | <span data-ttu-id="88089-391">1</span><span class="sxs-lookup"><span data-stu-id="88089-391">1</span></span>                       | <span data-ttu-id="88089-392">4</span><span class="sxs-lookup"><span data-stu-id="88089-392">4</span></span>     |  \| | <span data-ttu-id="88089-393">45</span><span class="sxs-lookup"><span data-stu-id="88089-393">45</span></span>    | <span data-ttu-id="88089-394">45</span><span class="sxs-lookup"><span data-stu-id="88089-394">45</span></span>                     | <span data-ttu-id="88089-395">0</span><span class="sxs-lookup"><span data-stu-id="88089-395">0</span></span>     | 

13. <span data-ttu-id="88089-396">Щелчок левой кнопкой на **новый текст** объекта, чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="88089-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="88089-397">В *панели Инспектора* задать *преобразования* компонент со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="88089-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="88089-398">Преобразование - *позиции*</span><span class="sxs-lookup"><span data-stu-id="88089-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="88089-399">Преобразование - *масштабирования*</span><span class="sxs-lookup"><span data-stu-id="88089-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="88089-400">**X**</span><span class="sxs-lookup"><span data-stu-id="88089-400">**X**</span></span> | <span data-ttu-id="88089-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="88089-401">**Y**</span></span>                  | <span data-ttu-id="88089-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="88089-402">**Z**</span></span> |  \| | <span data-ttu-id="88089-403">**X**</span><span class="sxs-lookup"><span data-stu-id="88089-403">**X**</span></span> | <span data-ttu-id="88089-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="88089-404">**Y**</span></span>               | <span data-ttu-id="88089-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="88089-405">**Z**</span></span> |
    | <span data-ttu-id="88089-406">-2</span><span class="sxs-lookup"><span data-stu-id="88089-406">-2</span></span>    | <span data-ttu-id="88089-407">6</span><span class="sxs-lookup"><span data-stu-id="88089-407">6</span></span>                      | <span data-ttu-id="88089-408">9</span><span class="sxs-lookup"><span data-stu-id="88089-408">9</span></span>     |  \| | <span data-ttu-id="88089-409">0.1</span><span class="sxs-lookup"><span data-stu-id="88089-409">0.1</span></span>   | <span data-ttu-id="88089-410">0.1</span><span class="sxs-lookup"><span data-stu-id="88089-410">0.1</span></span>                 | <span data-ttu-id="88089-411">0.1</span><span class="sxs-lookup"><span data-stu-id="88089-411">0.1</span></span>   | 

14. <span data-ttu-id="88089-412">Изменение **размер шрифта** в **Mesh текст** компонент **50**.</span><span class="sxs-lookup"><span data-stu-id="88089-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="88089-413">Изменение *имя* из **Mesh текст** объект **Диктовка текста**.</span><span class="sxs-lookup"><span data-stu-id="88089-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![Создание трехмерного объекта текста](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="88089-415">Структуры вашей иерархии панели теперь должна выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="88089-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![текст mesh в представлении сцены](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="88089-417">Окончательный сцены должен выглядеть как на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="88089-417">The final scene should look like the image below:</span></span>

    ![Представление сцены.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="88089-419">Глава 5 – создать класс MicrophoneManager</span><span class="sxs-lookup"><span data-stu-id="88089-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="88089-420">Первый скрипт, который вы собираетесь создать *MicrophoneManager* класса.</span><span class="sxs-lookup"><span data-stu-id="88089-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="88089-421">После этого вы создадите *LuisManager*, *поведений* класса и, наконец *помощи* класс (вы можете создать все эти now, то, что будет рассматриваться как связаться с каждой главы).</span><span class="sxs-lookup"><span data-stu-id="88089-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="88089-422">*MicrophoneManager* класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="88089-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="88089-423">Обнаружение записи устройству, подключенному к гарнитуры или machine (выбирается по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="88089-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="88089-424">Запись звука (голос) и использовать режим диктовки сохранит их в виде строки.</span><span class="sxs-lookup"><span data-stu-id="88089-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="88089-425">После приостановлена голоса, отправки диктофон, чтобы *LuisManager* класса.</span><span class="sxs-lookup"><span data-stu-id="88089-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="88089-426">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="88089-426">To create this class:</span></span> 

1.  <span data-ttu-id="88089-427">Щелкните правой кнопкой мыши в *проекта панели*, **Создать > Папка**.</span><span class="sxs-lookup"><span data-stu-id="88089-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="88089-428">Вызовите папке **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="88089-428">Call the folder **Scripts**.</span></span> 

    ![Создайте папку Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="88089-430">С помощью **сценариев** папка создана, дважды щелкните его, чтобы открыть.</span><span class="sxs-lookup"><span data-stu-id="88089-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="88089-431">Затем, внутри этой папки, щелкните правой кнопкой мыши **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="88089-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="88089-432">Назовите сценарий *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="88089-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="88089-433">Дважды щелкните *MicrophoneManager* чтобы открыть его с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="88089-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="88089-434">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="88089-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="88089-435">Затем добавьте следующие переменные внутри *MicrophoneManager* класса:</span><span class="sxs-lookup"><span data-stu-id="88089-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="88089-436">Код для *Awake()* и *Start()* методы теперь должен быть добавлен.</span><span class="sxs-lookup"><span data-stu-id="88089-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="88089-437">Это будет вызываться при инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="88089-437">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="88089-438">Теперь вам потребуется метод, который приложение использует для запуска и остановки записи голоса и передать его в *LuisManager* класса, который вы создадите в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="88089-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="88089-439">Добавить *обработчик диктовки* , будет вызываться при приостановке голоса.</span><span class="sxs-lookup"><span data-stu-id="88089-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="88089-440">Этот метод передает текст, диктовки *LuisManager* класса.</span><span class="sxs-lookup"><span data-stu-id="88089-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="88089-441">Удалить *Update()* метод, так как этот класс не будет его использовать.</span><span class="sxs-lookup"><span data-stu-id="88089-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="88089-442">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="88089-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="88089-443">На этом этапе вы заметите ошибку в *панель консоли редактора Unity*.</span><span class="sxs-lookup"><span data-stu-id="88089-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="88089-444">Это так, как код ссылается на *LuisManager* класс, который будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="88089-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="88089-445">Глава 6 – создать класс LUISManager</span><span class="sxs-lookup"><span data-stu-id="88089-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="88089-446">Пришло время для создания *LuisManager* класс, который сделает вызов службы Azure LUIS.</span><span class="sxs-lookup"><span data-stu-id="88089-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="88089-447">Этот класс предназначен для получения текста диктовки из *MicrophoneManager* класса и отправьте ее по адресу *API понимания языка Azure* для анализа.</span><span class="sxs-lookup"><span data-stu-id="88089-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="88089-448">Этот класс будет десериализовать *JSON* ответа и вызывать соответствующие методы *поведений* класс запускает действие.</span><span class="sxs-lookup"><span data-stu-id="88089-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="88089-449">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="88089-449">To create this class:</span></span> 

1.  <span data-ttu-id="88089-450">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="88089-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="88089-451">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="88089-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="88089-452">Назовите сценарий *LuisManager*.</span><span class="sxs-lookup"><span data-stu-id="88089-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="88089-453">Дважды щелкните сценарий, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="88089-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="88089-454">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="88089-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="88089-455">Сначала путем создания трех классов **внутри** *LuisManager* класса (в файле сценария, выше *Start()* метод), представляющие десериализованный Ответ JSON от Azure.</span><span class="sxs-lookup"><span data-stu-id="88089-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="88089-456">Добавьте следующие переменные внутри *LuisManager* класса:</span><span class="sxs-lookup"><span data-stu-id="88089-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="88089-457">Убедитесь, что теперь поместите конечной точке LUIS на (которая будет иметь через портал LUIS).</span><span class="sxs-lookup"><span data-stu-id="88089-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="88089-458">Код для *Awake()* теперь необходимо добавить метод.</span><span class="sxs-lookup"><span data-stu-id="88089-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="88089-459">Этот метод будет вызываться при инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="88089-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="88089-460">Теперь это приложение использует для отправки диктовки, полученные от методов *MicrophoneManager* класс *LUIS*и затем проверить и десериализировать ответа.</span><span class="sxs-lookup"><span data-stu-id="88089-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="88089-461">После определения значение Intent, и связанные сущности, они передаются в экземпляр *поведений* класс для активации требуемое действие.</span><span class="sxs-lookup"><span data-stu-id="88089-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="88089-462">Создайте новый метод с именем *AnalyseResponseElements()* , будет считывать итоговый *AnalysedQuery* и определять сущности.</span><span class="sxs-lookup"><span data-stu-id="88089-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="88089-463">После определения этих сущностей, они будут передаваться экземпляру *поведений* класс для использования в действиях.</span><span class="sxs-lookup"><span data-stu-id="88089-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognised intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="88089-464">Удалить *Start()* и *Update()* методы, так как этот класс не будет использовать их.</span><span class="sxs-lookup"><span data-stu-id="88089-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="88089-465">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="88089-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="88089-466">На этом этапе можно заметить несколько ошибок, появляющихся в *панель консоли редактора Unity*.</span><span class="sxs-lookup"><span data-stu-id="88089-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="88089-467">Это так, как код ссылается на *поведений* класс, который будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="88089-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="88089-468">Глава 7 – создать класс поведений</span><span class="sxs-lookup"><span data-stu-id="88089-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="88089-469">*Поведений* класс будет активировать действия, в которых используются сущности, предоставляемые *LuisManager* класса.</span><span class="sxs-lookup"><span data-stu-id="88089-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="88089-470">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="88089-470">To create this class:</span></span> 

1.  <span data-ttu-id="88089-471">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="88089-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="88089-472">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="88089-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="88089-473">Назовите сценарий *поведений*.</span><span class="sxs-lookup"><span data-stu-id="88089-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="88089-474">Дважды щелкните сценарий, чтобы открыть его с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="88089-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="88089-475">Затем добавьте следующие переменные внутри *поведений* класса:</span><span class="sxs-lookup"><span data-stu-id="88089-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="88089-476">Добавить *Awake()* код метода.</span><span class="sxs-lookup"><span data-stu-id="88089-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="88089-477">Этот метод будет вызываться при инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="88089-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="88089-478">Следующие методы вызываются *LuisManager* класс (который вы создали ранее) чтобы определить, какой объект является целевым объектом запроса и затем активировать соответствующее действие.</span><span class="sxs-lookup"><span data-stu-id="88089-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="88089-479">Добавить *FindTarget()* метод, чтобы определить, какие *объекты Gameobject* является целевым объектом текущей цели.</span><span class="sxs-lookup"><span data-stu-id="88089-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="88089-480">Этот метод по умолчанию целевой объект для *GameObject* «gazed» Если нет явной целевой объект определен в сущностях.</span><span class="sxs-lookup"><span data-stu-id="88089-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="88089-481">Удалить *Start()* и *Update()* методы, так как этот класс не будет использовать их.</span><span class="sxs-lookup"><span data-stu-id="88089-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="88089-482">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="88089-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="88089-483">Глава 8 – создать класс взглядом</span><span class="sxs-lookup"><span data-stu-id="88089-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="88089-484">Последний класс, который будет необходимо выполнить действия этого приложения является *помощи* класса.</span><span class="sxs-lookup"><span data-stu-id="88089-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="88089-485">Этот класс обновляет ссылку *GameObject* в настоящее время в визуальные указатели фокуса пользователя.</span><span class="sxs-lookup"><span data-stu-id="88089-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="88089-486">Для создания данного класса:</span><span class="sxs-lookup"><span data-stu-id="88089-486">To create this Class:</span></span> 

1.  <span data-ttu-id="88089-487">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="88089-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="88089-488">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="88089-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="88089-489">Назовите сценарий *помощи*.</span><span class="sxs-lookup"><span data-stu-id="88089-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="88089-490">Дважды щелкните сценарий, чтобы открыть его с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="88089-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="88089-491">Вставьте следующий код для данного класса:</span><span class="sxs-lookup"><span data-stu-id="88089-491">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="88089-492">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="88089-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="88089-493">Глава 9-завершения установки сцены</span><span class="sxs-lookup"><span data-stu-id="88089-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="88089-494">Чтобы завершить установку сцены, перетащите каждый скрипт, созданный из папки скриптов для **Main Camera** объекта в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="88089-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="88089-495">Выберите **Main Camera** и просмотрите *панели Инспектора*, можно увидеть каждый скрипт, который присоединен, и вы заметите, что существуют параметры для каждого сценария, которые будут устанавливаться.</span><span class="sxs-lookup"><span data-stu-id="88089-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![Задание целей ссылку камеры.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="88089-497">Чтобы правильно задать эти параметры, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="88089-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="88089-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="88089-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="88089-499">Из *панели иерархии*, перетащите **Диктовка текста** в коллекцию **Диктовка текста** поле значений параметров.</span><span class="sxs-lookup"><span data-stu-id="88089-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="88089-500">*Поведений*, из *панели иерархии*:</span><span class="sxs-lookup"><span data-stu-id="88089-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="88089-501">Перетащите **Sphere** в коллекцию *Sphere* "целевой объект ссылки".</span><span class="sxs-lookup"><span data-stu-id="88089-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="88089-502">Перетащите **цилиндра** в *цилиндра* "целевой объект ссылки".</span><span class="sxs-lookup"><span data-stu-id="88089-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="88089-503">Перетащите **куба** в *куба* "целевой объект ссылки".</span><span class="sxs-lookup"><span data-stu-id="88089-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="88089-504">*Помощи*:</span><span class="sxs-lookup"><span data-stu-id="88089-504">*Gaze*:</span></span>

        - <span data-ttu-id="88089-505">Задайте *помощи максимальное расстояние* для **300** (если это еще не сделано).</span><span class="sxs-lookup"><span data-stu-id="88089-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="88089-506">Результат должен выглядеть как на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="88089-506">The result should look like the image below:</span></span>

    ![Теперь отображается ссылка камеры целевые объекты, задайте.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="88089-508">Глава 10 – тест в редакторе Unity</span><span class="sxs-lookup"><span data-stu-id="88089-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="88089-509">Проверьте, что установки сцены реализуется надлежащим образом.</span><span class="sxs-lookup"><span data-stu-id="88089-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="88089-510">Убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="88089-510">Ensure that:</span></span>

-   <span data-ttu-id="88089-511">Все сценарии, присоединяются к **Main Camera** объекта.</span><span class="sxs-lookup"><span data-stu-id="88089-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="88089-512">Все поля в *главной панели Инспектора камеры* назначаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="88089-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="88089-513">Нажмите клавишу **воспроизведение** кнопку *редактора Unity*.</span><span class="sxs-lookup"><span data-stu-id="88089-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="88089-514">Приложения должны быть запущены в подключенных иммерсивных гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="88089-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="88089-515">Попробуйте выполните несколько фразы, например:</span><span class="sxs-lookup"><span data-stu-id="88089-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="88089-516">Если появится сообщение об ошибке, в консоли Unity о аудиоустройства по умолчанию изменение, сцены может не работать должным образом.</span><span class="sxs-lookup"><span data-stu-id="88089-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="88089-517">Это из-за способа на портале смешанной реальности имеет дело с встроенные микрофоны применяется, в которых они имеются.</span><span class="sxs-lookup"><span data-stu-id="88089-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="88089-518">Если эта ошибка возникает, просто остановить сцены и запустить снова и вещи должны работать как ожидалось.</span><span class="sxs-lookup"><span data-stu-id="88089-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="88089-519">Глава 11 – сборки и передайте решение универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="88089-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="88089-520">Когда вы убедились, что приложение работает в редакторе Unity, все готово для создания и развертывания.</span><span class="sxs-lookup"><span data-stu-id="88089-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="88089-521">Для сборки:</span><span class="sxs-lookup"><span data-stu-id="88089-521">To Build:</span></span>

1.  <span data-ttu-id="88089-522">Сохранить текущую сцену, щелкнув **файл > Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="88089-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="88089-523">Перейдите к **файл > Параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="88089-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="88089-524">Установка флажка поле, называемое **Unity C# проекты** (полезно для просмотра и отладки кода после создания проекта универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="88089-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="88089-525">Щелкните **добавьте откройте сцены**, затем нажмите кнопку **построения**.</span><span class="sxs-lookup"><span data-stu-id="88089-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Создать окно "Параметры"](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="88089-527">Вам будет предложено выбрать папку, где требуется выполнить сборку решения.</span><span class="sxs-lookup"><span data-stu-id="88089-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="88089-528">Создание *ПОСТРОЕНИЯ* папку и в этой папке создайте другую папку с соответствующим именем, по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="88089-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="88089-529">Нажмите кнопку **Выбор папки** для начала сборки в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="88089-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="88089-530">![Создайте папку Builds](images/AzureLabs-Lab3-44.png)
    ![фрагмент создаст папку](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="88089-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="88089-531">Один раз Unity завершил построение (может занять некоторое время), его следует открыть **проводнике** окно в папке построения.</span><span class="sxs-lookup"><span data-stu-id="88089-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="88089-532">Для развертывания на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="88089-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="88089-533">В *Visual Studio*, откройте файл решения, созданной в [предыдущей главе](#chapter-10--test-in-the-unity-editor).</span><span class="sxs-lookup"><span data-stu-id="88089-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="88089-534">В **платформа решения**выберите **x86**, **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="88089-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="88089-535">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="88089-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="88089-536">Для Microsoft HoloLens, может быть проще устанавливать равным *удаленный компьютер*, таким образом, не связанном устройстве на компьютер.</span><span class="sxs-lookup"><span data-stu-id="88089-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="88089-537">Однако необходимо будет выполнить следующее:</span><span class="sxs-lookup"><span data-stu-id="88089-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="88089-538">Знать **IP-адрес** из HoloLens, которую можно найти в *параметры > сеть и Интернет > Wi-Fi > Дополнительно*; IPv4 — это адрес, следует использовать.</span><span class="sxs-lookup"><span data-stu-id="88089-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="88089-539">Убедитесь, **режим разработчика** — **на**; найдено в *параметры > обновление и безопасность > для разработчиков*.</span><span class="sxs-lookup"><span data-stu-id="88089-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Развертывание приложения](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="88089-541">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на компьютер.</span><span class="sxs-lookup"><span data-stu-id="88089-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="88089-542">Приложения должны появиться в списке установленных приложений, Готово к запуску!</span><span class="sxs-lookup"><span data-stu-id="88089-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="88089-543">После запуска приложения будет предложено авторизовать доступ к _"микрофон"_.</span><span class="sxs-lookup"><span data-stu-id="88089-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="88089-544">Используйте *контроллеров движения*, или *голосовой ввод*, или *клавиатуры* клавишу **Да** кнопки.</span><span class="sxs-lookup"><span data-stu-id="88089-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="88089-545">Глава 12 – улучшение службе LUIS</span><span class="sxs-lookup"><span data-stu-id="88089-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="88089-546">В этой главе чрезвычайно важна и может потребоваться быть просмотрен на несколько раз, так как это поможет повысить точность службе LUIS: Убедитесь, завершения этой операции.</span><span class="sxs-lookup"><span data-stu-id="88089-546">This chapter is incredibly important, and may need to be interated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="88089-547">Чтобы повысить уровень понимания, предоставляемые LUIS, вам потребуется записать новый фразы и использовать их для повторного обучения приложением LUIS.</span><span class="sxs-lookup"><span data-stu-id="88089-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="88089-548">Например может обучения LUIS для понимания «Increase» и «Преобразования», но не требуется знать слова, такие как «Увеличить» приложение?</span><span class="sxs-lookup"><span data-stu-id="88089-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="88089-549">После использования приложения несколько раз, все, что вы сказали будут собраны LUIS и доступны на ПОРТАЛЕ LUIS.</span><span class="sxs-lookup"><span data-stu-id="88089-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="88089-550">Перейдите к приложению портала следуя инструкциям из этого [ССЫЛКУ](https://www.luis.ai/home)и вход в систему.</span><span class="sxs-lookup"><span data-stu-id="88089-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="88089-551">Когда вы выполняете вход с использованием учетных данных MS, нажмите кнопку вашей *имя_приложения*.</span><span class="sxs-lookup"><span data-stu-id="88089-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="88089-552">Нажмите кнопку **просмотрите фразы конечной точки** кнопка в левой части страницы.</span><span class="sxs-lookup"><span data-stu-id="88089-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Просмотрите фразы](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="88089-554">Будет показан список фразы, которые были отправлены в LUIS в смешанной реальности приложения.</span><span class="sxs-lookup"><span data-stu-id="88089-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Список фразы](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="88089-556">Обратите внимание, некоторые выделенные *сущностей*.</span><span class="sxs-lookup"><span data-stu-id="88089-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="88089-557">Навести указатель мыши на каждый выделенное слово, можно просмотреть каждый Utterance и определить, какие сущности был распознан правильно, что сущности — это не так, а какие сущности будут отсутствовать.</span><span class="sxs-lookup"><span data-stu-id="88089-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="88089-558">В приведенном выше примере он найден, что слово «spear» были выделены как целевой объект, поэтому ее необходимо исправить ошибку, что можно сделать, наведя word с помощью мыши и выбрав **удалить метку**.</span><span class="sxs-lookup"><span data-stu-id="88089-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="88089-559">![Проверьте фразы](images/AzureLabs-Lab3-49.png)
![удалить изображения подписи](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="88089-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="88089-560">Если вы нашли фразы, которые полностью неверны, их можно удалить с помощью **удалить** кнопку в правой части экрана.</span><span class="sxs-lookup"><span data-stu-id="88089-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Удалите неправильный фразы](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="88089-562">Или если вы считаете, что LUIS Utterance правильную интерпретацию, можно проверить с помощью его основные сведения о **добавить к краю намерение** кнопки.</span><span class="sxs-lookup"><span data-stu-id="88089-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Добавьте в выровненных намерения](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="88089-564">После сортировки всех отображаемых фразы, попробуйте и перезагрузите страницу, чтобы увидеть, если сведения доступны.</span><span class="sxs-lookup"><span data-stu-id="88089-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="88089-565">Очень важно повторите эту процедуру столько раз, как можно ближе к Углубленное освоение приложения.</span><span class="sxs-lookup"><span data-stu-id="88089-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="88089-566">**Веселитесь!**</span><span class="sxs-lookup"><span data-stu-id="88089-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="88089-567">Встроенная LUIS готового приложения</span><span class="sxs-lookup"><span data-stu-id="88089-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="88089-568">Поздравляем, вы создали приложение смешанной реальности, использующем присоединение к Azure интеллектуальная служба анализа языка, чтобы понять, что говорит пользователь и act на основе этих данных.</span><span class="sxs-lookup"><span data-stu-id="88089-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![Результат лаборатории](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="88089-570">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="88089-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="88089-571">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="88089-571">Exercise 1</span></span>

<span data-ttu-id="88089-572">При использовании этого приложения вы можете заметить, что при помощи в объекте, Floor и попросите изменить его цвет, она сделает это.</span><span class="sxs-lookup"><span data-stu-id="88089-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="88089-573">Можно работать как остановить выполнение приложения изменения цвета Floor?</span><span class="sxs-lookup"><span data-stu-id="88089-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="88089-574">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="88089-574">Exercise 2</span></span>

<span data-ttu-id="88089-575">Попробуйте расширение возможностей приложения и LUIS, добавив дополнительные функциональные возможности для объектов в сцене; Например создайте новые объекты в взглядом точку нажатия, в зависимости от того, пользователь говорит, а затем смогут использовать эти объекты вместе с текущей объектов сцены, с помощью существующих команд.</span><span class="sxs-lookup"><span data-stu-id="88089-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
