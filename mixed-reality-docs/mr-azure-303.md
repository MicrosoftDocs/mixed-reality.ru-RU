---
title: MR и Azure 303 — понимание естественного языка (LUIS)
description: Пройдите этот курс, чтобы узнать, как реализовать службу Azure Language Understanding Intelligence (LUIS) в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, Служба анализа языка, Luis, hololens, иммерсивное, VR
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926807"
---
>[!NOTE]
><span data-ttu-id="5914a-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5914a-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="5914a-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="5914a-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="5914a-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5914a-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="5914a-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="5914a-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="5914a-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5914a-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="5914a-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="5914a-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="5914a-110">MR и Azure 303: понимание естественного языка (LUIS)</span><span class="sxs-lookup"><span data-stu-id="5914a-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="5914a-111">В этом курсе вы узнаете, как интегрировать Language Understanding в приложение смешанной реальности с помощью Cognitive Services Azure с API распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="5914a-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![результат лаборатории](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="5914a-113">*Language Understanding (Luis)* — это Microsoft Azure служба, которая предоставляет приложениям возможность принимать значения из вводимых пользователем данных, например, путем извлечения того, что может потребоваться пользователю, в отдельных словах.</span><span class="sxs-lookup"><span data-stu-id="5914a-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="5914a-114">Это достигается благодаря машинному обучению, которое понимает и изучает входные данные, а затем может ответить на подробные и релевантные сведения.</span><span class="sxs-lookup"><span data-stu-id="5914a-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="5914a-115">Дополнительные сведения см. на [странице Language Understanding Azure (Luis)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="5914a-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="5914a-116">Прополнив этот курс, вы получите иммерсивное приложение для наушников, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="5914a-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="5914a-117">Запись речевого ввода пользователя с помощью микрофона, подключенного к иммерсивное гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="5914a-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="5914a-118">Отправка захваченной диктовки *Language Understanding Intelligent Service Azure* (*Luis*).</span><span class="sxs-lookup"><span data-stu-id="5914a-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="5914a-119">LUIS извлечение значения из сведений об отправке, которые будут проанализированы, и попытаться определить цель запроса пользователя.</span><span class="sxs-lookup"><span data-stu-id="5914a-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="5914a-120">Разработка будет включать в себя создание приложения, в котором пользователь сможет использовать голоса и (или) Взгляните, чтобы изменить размер и цвет объектов в сцене.</span><span class="sxs-lookup"><span data-stu-id="5914a-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="5914a-121">Использование контроллеров движения не будет охвачено.</span><span class="sxs-lookup"><span data-stu-id="5914a-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="5914a-122">В приложении вы будете выполнять интеграцию результатов с вашей структурой.</span><span class="sxs-lookup"><span data-stu-id="5914a-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="5914a-123">Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="5914a-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="5914a-124">Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="5914a-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="5914a-125">Будьте готовы обучить LUIS несколько раз, как описано в [главе 12](#chapter-12--improving-your-luis-service).</span><span class="sxs-lookup"><span data-stu-id="5914a-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="5914a-126">Вы получите лучшие результаты, которые больше LUIS обучены.</span><span class="sxs-lookup"><span data-stu-id="5914a-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="5914a-127">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="5914a-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="5914a-128">Хождение</span><span class="sxs-lookup"><span data-stu-id="5914a-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="5914a-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="5914a-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="5914a-130"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="5914a-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="5914a-131">MR и Azure 303: понимание естественного языка (LUIS)</span><span class="sxs-lookup"><span data-stu-id="5914a-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="5914a-132">✔️</span><span class="sxs-lookup"><span data-stu-id="5914a-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="5914a-133">✔️</span><span class="sxs-lookup"><span data-stu-id="5914a-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="5914a-134">Хотя этот курс в основном ориентирован на гарнитуры Windows Mixed Reality (VR), вы также можете применить сведения, которые вы узнаете в этом курсе, к Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5914a-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="5914a-135">Как вы пройдете вместе с курсом, вы увидите примечания о любых изменениях, которые могут потребоваться для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5914a-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="5914a-136">При использовании HoloLens вы можете заметить некоторые эхо во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="5914a-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5914a-137">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="5914a-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="5914a-138">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="5914a-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="5914a-139">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено во время написания статьи (Май 2018).</span><span class="sxs-lookup"><span data-stu-id="5914a-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="5914a-140">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем показано ниже.</span><span class="sxs-lookup"><span data-stu-id="5914a-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="5914a-141">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="5914a-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="5914a-142">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="5914a-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="5914a-143">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="5914a-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="5914a-144">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="5914a-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="5914a-145">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="5914a-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="5914a-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5914a-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="5914a-147">Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="5914a-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="5914a-148">Набор наушников со встроенным микрофоном (если у гарнитуры нет встроенного MIC и динамиков);</span><span class="sxs-lookup"><span data-stu-id="5914a-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="5914a-149">Доступ к Интернету для установки Azure и извлечения LUIS</span><span class="sxs-lookup"><span data-stu-id="5914a-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="5914a-150">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="5914a-150">Before you start</span></span>

1.  <span data-ttu-id="5914a-151">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="5914a-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="5914a-152">Чтобы разрешить компьютеру Включить диктовку, перейдите в раздел **Параметры Windows > конфиденциальность > речи, ввод рукописных данных & ввода** и нажмите кнопку **включить речевые службы и ввести предложения**.</span><span class="sxs-lookup"><span data-stu-id="5914a-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="5914a-153">Код в этом учебнике позволит вам записывать данные из набора устройств на основе **микрофона по умолчанию** на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5914a-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="5914a-154">Убедитесь, что в качестве микрофона по умолчанию выбрано устройство, которое вы хотите использовать для записи голоса.</span><span class="sxs-lookup"><span data-stu-id="5914a-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="5914a-155">Если у гарнитуры есть встроенный микрофон, убедитесь, что параметр *"при износе гарнитуры, переключиться на микрофон гарнитуры"* включен в параметрах *портала смешанной реальности* .</span><span class="sxs-lookup"><span data-stu-id="5914a-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Настройка иммерсивного головного телефона](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="5914a-157">Глава 1 — Настройка портала Azure</span><span class="sxs-lookup"><span data-stu-id="5914a-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="5914a-158">Чтобы использовать службу *Language Understanding* в Azure, необходимо настроить экземпляр службы, чтобы сделать ее доступной для приложения.</span><span class="sxs-lookup"><span data-stu-id="5914a-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="5914a-159">Войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="5914a-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="5914a-160">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="5914a-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="5914a-161">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="5914a-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="5914a-162">Войдя в систему, щелкните New ( **создать** ) в левом верхнем углу, найдите *Language Understanding*и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="5914a-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![Создание ресурса LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="5914a-164">Слово **New** может быть заменено на **создать ресурс**в новых порталах.</span><span class="sxs-lookup"><span data-stu-id="5914a-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="5914a-165">На новой странице справа будет представлено описание службы Language Understanding.</span><span class="sxs-lookup"><span data-stu-id="5914a-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="5914a-166">В нижнем левом углу этой страницы нажмите кнопку **создать** , чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="5914a-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Создание службы LUIS — Юридическая информация](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="5914a-168">После нажатия кнопки Создать:</span><span class="sxs-lookup"><span data-stu-id="5914a-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="5914a-169">Вставьте нужное **имя** для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="5914a-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="5914a-170">Выберите **подписку**.</span><span class="sxs-lookup"><span data-stu-id="5914a-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="5914a-171">Выберите **ценовую категорию** , подходящую для вас. Если вы впервые создаете *службу Luis*, вам будет доступен бесплатный уровень (с именем F0).</span><span class="sxs-lookup"><span data-stu-id="5914a-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="5914a-172">Для этого курса Свободное выделение должно быть больше, чем достаточно.</span><span class="sxs-lookup"><span data-stu-id="5914a-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="5914a-173">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="5914a-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="5914a-174">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="5914a-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="5914a-175">Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="5914a-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="5914a-176">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, обратитесь [к статье о группе ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="5914a-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="5914a-177">Определите **Расположение** группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="5914a-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="5914a-178">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="5914a-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="5914a-179">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="5914a-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="5914a-180">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="5914a-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="5914a-181">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="5914a-181">Select **Create**.</span></span>

        ![Создание службы LUIS. ввод пользователя](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="5914a-183">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="5914a-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="5914a-184">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="5914a-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Новый образ уведомлений Azure](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="5914a-186">Щелкните уведомление, чтобы просмотреть новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="5914a-186">Click on the notification to explore your new Service instance.</span></span>

    ![Уведомление об успешном создании ресурса](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="5914a-188">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="5914a-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="5914a-189">Вы будете перенаправлены на новый экземпляр службы LUIS.</span><span class="sxs-lookup"><span data-stu-id="5914a-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![Доступ к ключам LUIS](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="5914a-191">В рамках этого руководства приложение должно будет вызывать службу, что выполняется с помощью ключа подписки вашей службы.</span><span class="sxs-lookup"><span data-stu-id="5914a-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="5914a-192">На странице *быстрого запуска* службы *API Luis* перейдите к первому шагу, *Возьмите ключи*и щелкните **ключи** (это можно также сделать, щелкнув синие клавиши-гиперссылки, расположенные в меню навигации службы, обозначенном значком ключа).</span><span class="sxs-lookup"><span data-stu-id="5914a-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="5914a-193">При этом будут раскрыты *ключи*службы.</span><span class="sxs-lookup"><span data-stu-id="5914a-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="5914a-194">Сделайте копию одного из отображаемых ключей, так как это потребуется позже в проекте.</span><span class="sxs-lookup"><span data-stu-id="5914a-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="5914a-195">На странице *Служба* щелкните *Language Understanding портал* для перенаправления на веб-страницу, которая будет использоваться для создания новой службы в приложении Luis.</span><span class="sxs-lookup"><span data-stu-id="5914a-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="5914a-196">Глава 2 — портал Language Understanding</span><span class="sxs-lookup"><span data-stu-id="5914a-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="5914a-197">В этом разделе вы узнаете, как создать приложение LUIS на портале LUIS.</span><span class="sxs-lookup"><span data-stu-id="5914a-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="5914a-198">Имейте в виду, что настройка *сущностей*, *целей*и *фразы продолжительностью* в этой главе является только первым шагом в создании службы Luis. Вам также потребуется заново обучить службу, чтобы сделать ее более точной.</span><span class="sxs-lookup"><span data-stu-id="5914a-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="5914a-199">Переобучение службы описано в [последней главе](#chapter-12--improving-your-luis-service) этого курса, поэтому убедитесь, что вы завершили его.</span><span class="sxs-lookup"><span data-stu-id="5914a-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="5914a-200">При достижении *Language Understanding портала*вам может потребоваться выполнить вход, если вы еще не сделали этого, с теми же учетными данными, что и у портал Azure.</span><span class="sxs-lookup"><span data-stu-id="5914a-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![Страница входа в LUIS](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="5914a-202">Если вы впервые используете LUIS, необходимо прокрутить вниз до нижней части страницы приветствия, чтобы найти и нажать кнопку **создать приложение Luis** .</span><span class="sxs-lookup"><span data-stu-id="5914a-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![Страница создания приложения LUIS](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="5914a-204">После входа в систему щелкните **Мои приложения** (если вы не в этом разделе сейчас).</span><span class="sxs-lookup"><span data-stu-id="5914a-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="5914a-205">Затем можно щелкнуть **создать новое приложение**.</span><span class="sxs-lookup"><span data-stu-id="5914a-205">You can then click on **Create new app**.</span></span>

    ![LUIS — образ "Мои приложения"](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="5914a-207">Присвойте *имя*приложению.</span><span class="sxs-lookup"><span data-stu-id="5914a-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="5914a-208">Если ваше приложение должно понимать язык, отличающийся от английского, следует изменить язык *и региональные параметры* на соответствующий.</span><span class="sxs-lookup"><span data-stu-id="5914a-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="5914a-209">Здесь можно также добавить *Описание* нового приложения Luis.</span><span class="sxs-lookup"><span data-stu-id="5914a-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS — создание нового приложения](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="5914a-211">После нажатия кнопки " **Готово**" вы введете страницу *сборки* нового приложения *Luis* .</span><span class="sxs-lookup"><span data-stu-id="5914a-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="5914a-212">Существует несколько важных концепций, которые необходимо понять:</span><span class="sxs-lookup"><span data-stu-id="5914a-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="5914a-213">*Намерение*представляет метод, который будет вызываться после запроса от пользователя.</span><span class="sxs-lookup"><span data-stu-id="5914a-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="5914a-214">*Намерение* может иметь одну или несколько *сущностей*.</span><span class="sxs-lookup"><span data-stu-id="5914a-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="5914a-215">*Entity*— это компонент запроса, который описывает сведения, относящиеся к *намерениям*.</span><span class="sxs-lookup"><span data-stu-id="5914a-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="5914a-216">*Фразы продолжительностью*— примеры запросов, предоставляемых разработчиком, которые Luis будут использовать для обучения.</span><span class="sxs-lookup"><span data-stu-id="5914a-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="5914a-217">Если эти понятия не вполне понятны, не беспокойтесь, так как этот курс прояснить их в этой главе.</span><span class="sxs-lookup"><span data-stu-id="5914a-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="5914a-218">Начнем с создания *сущностей* , необходимых для создания этого курса.</span><span class="sxs-lookup"><span data-stu-id="5914a-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="5914a-219">В левой части страницы щелкните *сущности*, а затем — **создать новую сущность**.</span><span class="sxs-lookup"><span data-stu-id="5914a-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Создать новую сущность](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="5914a-221">Вызовите новый *Цвет*сущности, задайте для его типа значение *Simple*, а затем нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="5914a-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Создание простого объекта-цвета](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="5914a-223">Повторите эту процедуру, чтобы создать три (3) более простые сущности с именем:</span><span class="sxs-lookup"><span data-stu-id="5914a-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="5914a-224">*Размер*</span><span class="sxs-lookup"><span data-stu-id="5914a-224">*upsize*</span></span>
    -   <span data-ttu-id="5914a-225">*уменьшать их размер*</span><span class="sxs-lookup"><span data-stu-id="5914a-225">*downsize*</span></span>
    -   <span data-ttu-id="5914a-226">*мишень*</span><span class="sxs-lookup"><span data-stu-id="5914a-226">*target*</span></span>

<span data-ttu-id="5914a-227">Результат должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5914a-227">The result should look like the image below:</span></span>

![Результат создания сущности](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="5914a-229">На этом этапе можно приступить к созданию *целей*.</span><span class="sxs-lookup"><span data-stu-id="5914a-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="5914a-230">Не удаляйте цель **None** .</span><span class="sxs-lookup"><span data-stu-id="5914a-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="5914a-231">В левой части страницы щелкните **цели, а затем —** **создать новое намерение**.</span><span class="sxs-lookup"><span data-stu-id="5914a-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Создание новых целей](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="5914a-233">Вызовите новый *намеренный* **чанжеобжектколор**.</span><span class="sxs-lookup"><span data-stu-id="5914a-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5914a-234">Это имя *намерения* используется в коде далее в этом курсе, поэтому для получения наилучших результатов используйте это имя точно так же, как указано.</span><span class="sxs-lookup"><span data-stu-id="5914a-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="5914a-235">Подтвердите имя, которое будет направляться на страницу «способы».</span><span class="sxs-lookup"><span data-stu-id="5914a-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS — страница «намерения»](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="5914a-237">Вы заметите, что у вас есть текстовое поле с предложением ввести 5 или более различных *фразы продолжительностью*.</span><span class="sxs-lookup"><span data-stu-id="5914a-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="5914a-238">LUIS преобразует все фразы продолжительностью в нижний регистр.</span><span class="sxs-lookup"><span data-stu-id="5914a-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="5914a-239">Вставьте следующий *utterance* в верхнее текстовое поле (в настоящее время с текстом *типа 5 примеров...*</span><span class="sxs-lookup"><span data-stu-id="5914a-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="5914a-240">) и нажмите клавишу **Ввод**:</span><span class="sxs-lookup"><span data-stu-id="5914a-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="5914a-241">Вы увидите, что новый *utterance* появится в списке под.</span><span class="sxs-lookup"><span data-stu-id="5914a-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="5914a-242">После того же процесса вставьте следующие шесть (6) фразы продолжительностью:</span><span class="sxs-lookup"><span data-stu-id="5914a-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="5914a-243">Для каждого созданного utterance необходимо указать, какие слова должны использоваться LUIS в качестве сущностей.</span><span class="sxs-lookup"><span data-stu-id="5914a-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="5914a-244">В этом примере необходимо пометить все цвета как сущность *цвета* и все возможные ссылки на целевой объект в качестве *целевой* сущности.</span><span class="sxs-lookup"><span data-stu-id="5914a-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="5914a-245">Для этого попробуйте щелкнуть *цилиндр* на слове в первом utterance и выбрать *целевой объект*.</span><span class="sxs-lookup"><span data-stu-id="5914a-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Определяет целевые объекты utterance](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="5914a-247">Теперь щелкните слово *Red* в первом utterance и выберите *Цвет*.</span><span class="sxs-lookup"><span data-stu-id="5914a-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Поиск сущностей utterance](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="5914a-249">Метка Следующая строка также, где *куб* должен быть *целевым объектом*, а *черный* должен быть *цветом*.</span><span class="sxs-lookup"><span data-stu-id="5914a-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="5914a-250">Также обратите внимание на использование слов *this*, *"IT*" и *"this Object"* , которые мы предоставляем, поэтому для неконкретных целевых типов также доступны.</span><span class="sxs-lookup"><span data-stu-id="5914a-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="5914a-251">Повторите описанный выше процесс, пока все фразы продолжительностью не помечаются сущностями.</span><span class="sxs-lookup"><span data-stu-id="5914a-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="5914a-252">Если вам нужна помощь, см. рисунок ниже.</span><span class="sxs-lookup"><span data-stu-id="5914a-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="5914a-253">При выборе слов для пометки в качестве сущностей:</span><span class="sxs-lookup"><span data-stu-id="5914a-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="5914a-254">Для отдельных слов просто щелкните их.</span><span class="sxs-lookup"><span data-stu-id="5914a-254">For single words just click them.</span></span>
    > - <span data-ttu-id="5914a-255">Для набора из двух или более слов щелкните в начале, а затем в конце набора.</span><span class="sxs-lookup"><span data-stu-id="5914a-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5914a-256">Для переключения между **представлениями сущностей и маркеров**можно использовать выключатель *представления маркеров* .</span><span class="sxs-lookup"><span data-stu-id="5914a-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="5914a-257">Результаты должны быть показаны на приведенных ниже изображениях, в которых отображается **представление "сущности и маркеры**":</span><span class="sxs-lookup"><span data-stu-id="5914a-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Маркеры & представления сущностей](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="5914a-259">На этом этапе нажмите кнопку " **обучение** " в правом верхнем углу страницы и дождитесь, чтобы индикатор небольшого круга был включен зеленым цветом.</span><span class="sxs-lookup"><span data-stu-id="5914a-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="5914a-260">Это означает, что LUIS успешно обучена для распознавания этой цели.</span><span class="sxs-lookup"><span data-stu-id="5914a-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![Обучение LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="5914a-262">В качестве упражнения создайте новую цель с именем **чанжеобжектсизе**, используя *целевые*объекты, *Размер*и *уменьшать их размер*.</span><span class="sxs-lookup"><span data-stu-id="5914a-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="5914a-263">Следуя тому же процессу, что и в предыдущем намерении, вставьте следующие восемь (8) фразы продолжительностью для изменения *размера* :</span><span class="sxs-lookup"><span data-stu-id="5914a-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

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

23. <span data-ttu-id="5914a-264">Результат должен быть подобен показанному на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="5914a-264">The result should be like the one in the image below:</span></span>

    ![Настройка маркеров и сущностей Чанжеобжектсизе](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="5914a-266">После создания и обучения обоих целей, **чанжеобжектколор** и **чанжеобжектсизе**, нажмите кнопку **опубликовать** в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="5914a-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![Публикация службы LUIS](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="5914a-268">На странице *Публикация* вы завершите и опубликуете приложение Luis, чтобы к нему можно было получить доступ с помощью вашего кода.</span><span class="sxs-lookup"><span data-stu-id="5914a-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="5914a-269">Установите в раскрывающемся списке *опубликовать* значение как **Рабочая**.</span><span class="sxs-lookup"><span data-stu-id="5914a-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="5914a-270">Задайте *часовой* пояс в качестве часового пояса.</span><span class="sxs-lookup"><span data-stu-id="5914a-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="5914a-271">Установите флажок **все оценки предполагаемых намерения**.</span><span class="sxs-lookup"><span data-stu-id="5914a-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="5914a-272">Щелкните **опубликовать в рабочем слоте**.</span><span class="sxs-lookup"><span data-stu-id="5914a-272">Click on **Publish to Production Slot**.</span></span>

        ![Параметры публикации](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="5914a-274">В разделе *ресурсы и ключи*:</span><span class="sxs-lookup"><span data-stu-id="5914a-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="5914a-275">Выберите регион, заданный для экземпляра службы на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="5914a-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="5914a-276">Обратите внимание на элемент **Starter_Key** ниже, игнорируя его.</span><span class="sxs-lookup"><span data-stu-id="5914a-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="5914a-277">Щелкните **Добавить ключ** и вставьте *ключ* , полученный на портале Azure, при создании экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="5914a-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="5914a-278">Если Azure и портал LUIS вошли в систему одного и того же пользователя, вам будут предоставлены раскрывающиеся меню для *имени клиента*, *имени подписки*и *ключа* , которые вы хотите использовать (имя будет совпадать с именем, которое вы указали ранее на портале Azure).</span><span class="sxs-lookup"><span data-stu-id="5914a-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="5914a-279">В нижней *конечной точке*Возьмите копию конечной точки, соответствующей вставленному ключу, вскоре вы будете использовать его в своем коде.</span><span class="sxs-lookup"><span data-stu-id="5914a-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="5914a-280">Глава 3 — Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="5914a-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="5914a-281">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="5914a-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="5914a-282">Откройте *Unity* и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="5914a-282">Open *Unity* and click **New**.</span></span> 

    ![Запуск нового проекта Unity.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="5914a-284">Теперь необходимо указать имя проекта Unity, вставить **MR_LUIS**.</span><span class="sxs-lookup"><span data-stu-id="5914a-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="5914a-285">Убедитесь, что для типа проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="5914a-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="5914a-286">Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="5914a-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="5914a-287">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="5914a-287">Then, click **Create project**.</span></span>

    ![Укажите сведения о новом проекте Unity.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="5914a-289">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="5914a-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="5914a-290">Перейдите к разделу Изменение параметров >, а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="5914a-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="5914a-291">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="5914a-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="5914a-292">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="5914a-292">Close the **Preferences** window.</span></span>

    ![Обновить настройки редактора скриптов.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="5914a-294">Затем перейдите в раздел **файл > параметры сборки** и переключите платформу на **универсальная платформа Windows**, нажав кнопку **коммутатора платформы** .</span><span class="sxs-lookup"><span data-stu-id="5914a-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Окно "параметры сборки". Переключите платформу в UWP.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="5914a-296">Перейдите в раздел **файл > параметры сборки** и убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="5914a-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="5914a-297">**Целевое устройство** настроено для **любого устройства**</span><span class="sxs-lookup"><span data-stu-id="5914a-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="5914a-298">Для Microsoft HoloLens задайте для параметра **целевое устройство** значение *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="5914a-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="5914a-299">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="5914a-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="5914a-300">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="5914a-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="5914a-301">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="5914a-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="5914a-302">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="5914a-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="5914a-303">Сохраните сцену и добавьте ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="5914a-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="5914a-304">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="5914a-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="5914a-305">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="5914a-305">A save window will appear.</span></span>
        
            ![Нажмите кнопку Добавить кнопку "открыть сцены"](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="5914a-307">Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="5914a-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создать новую папку скриптов](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="5914a-309">Откройте только что созданную папку **сцены** , а затем в поле *имя файла*: введите **MR_LuisScene**, а затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="5914a-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Присвойте имя новой сцене.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="5914a-311">Оставшиеся параметры, в *параметрах сборки*, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5914a-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="5914a-312">В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* .</span><span class="sxs-lookup"><span data-stu-id="5914a-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Откройте параметры проигрывателя.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="5914a-314">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="5914a-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="5914a-315">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="5914a-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="5914a-316">**Версия среды выполнения сценариев** должна быть **стабильной** (эквивалент .NET 3,5).</span><span class="sxs-lookup"><span data-stu-id="5914a-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="5914a-317">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="5914a-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="5914a-318">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="5914a-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Обновите другие параметры.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="5914a-320">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="5914a-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="5914a-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="5914a-321">**InternetClient**</span></span>
        2. <span data-ttu-id="5914a-322">**Звук**</span><span class="sxs-lookup"><span data-stu-id="5914a-322">**Microphone**</span></span>

            ![Обновляются параметры публикации.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="5914a-324">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="5914a-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Обновите параметры X R.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="5914a-326">Назад в *параметрах сборки* проект _Unity C#_  больше не является серым. Установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="5914a-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="5914a-327">Закройте окно параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="5914a-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="5914a-328">Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="5914a-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="5914a-329">Глава 4 — Создание сцены</span><span class="sxs-lookup"><span data-stu-id="5914a-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5914a-330">Если вы хотите пропустить компонент *установки Unity, установленный* в этом курсе, и продолжить работу с кодом, скачайте этот файл [. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), импортируйте его в проект как [пользовательский пакет](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте в [главе 5](#chapter-5--create-the-microphonemanager-class).</span><span class="sxs-lookup"><span data-stu-id="5914a-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="5914a-331">Щелкните правой кнопкой мыши пустую область *панели Иерархия*в разделе **трехмерный объект**, добавьте **плоскость**.</span><span class="sxs-lookup"><span data-stu-id="5914a-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Создайте плоскость.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="5914a-333">Имейте в виду, что если щелкнуть правой кнопкой мыши в *иерархии* , чтобы создать больше объектов, то если последний объект по-прежнему выбран, то выбранный объект будет родительским для нового объекта.</span><span class="sxs-lookup"><span data-stu-id="5914a-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="5914a-334">Избегайте щелчка левой кнопкой мыши в пустом пространстве внутри иерархии, а затем щелкните правой клавишей.</span><span class="sxs-lookup"><span data-stu-id="5914a-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="5914a-335">Повторите описанную выше процедуру, чтобы добавить следующие объекты:</span><span class="sxs-lookup"><span data-stu-id="5914a-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="5914a-336">*Сфере*</span><span class="sxs-lookup"><span data-stu-id="5914a-336">*Sphere*</span></span>
    2. <span data-ttu-id="5914a-337">*Виде*</span><span class="sxs-lookup"><span data-stu-id="5914a-337">*Cylinder*</span></span>
    3. <span data-ttu-id="5914a-338">*Куба*</span><span class="sxs-lookup"><span data-stu-id="5914a-338">*Cube*</span></span>
    4. <span data-ttu-id="5914a-339">*Объемный текст*</span><span class="sxs-lookup"><span data-stu-id="5914a-339">*3D Text*</span></span>

4.  <span data-ttu-id="5914a-340">Итоговая *Иерархия* сцены должна быть похожа на показанную на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="5914a-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Настройка иерархии сцены.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="5914a-342">Щелкните на **основной камере** , чтобы выбрать ее. на *панели инспектора* вы увидите объект Camera со всеми компонентами.</span><span class="sxs-lookup"><span data-stu-id="5914a-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="5914a-343">Нажмите кнопку **Добавить компонент** , расположенную в самом низу *панели инспектора*.</span><span class="sxs-lookup"><span data-stu-id="5914a-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Добавить источник звука](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="5914a-345">Найдите компонент « *источник звука*», как показано выше.</span><span class="sxs-lookup"><span data-stu-id="5914a-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="5914a-346">Также убедитесь, что компонент *преобразования* основной камеры имеет значение (0, 0, 0). это можно сделать, нажав значок **шестеренки** рядом с компонентом *преобразования* камеры и выбрав **Сброс**.</span><span class="sxs-lookup"><span data-stu-id="5914a-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="5914a-347">Компонент *преобразования* должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5914a-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="5914a-348">Для параметра *положением* задано значение **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="5914a-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="5914a-349">Для *вращения* задано значение **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="5914a-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="5914a-350">Для Microsoft HoloLens необходимо также изменить следующие компоненты, которые являются частью компонента **камеры** , расположенного на **основной камере**:</span><span class="sxs-lookup"><span data-stu-id="5914a-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="5914a-351">**Снять флаги:** Сплошной цвет.</span><span class="sxs-lookup"><span data-stu-id="5914a-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="5914a-352">**Фоновый режим** "Черный, альфа 0" — шестнадцатеричный цвет: #00000000.</span><span class="sxs-lookup"><span data-stu-id="5914a-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="5914a-353">Щелкните **плоскость** левой кнопкой мыши, чтобы выбрать ее.</span><span class="sxs-lookup"><span data-stu-id="5914a-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="5914a-354">На *панели инспектора* установите компонент *преобразования* со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="5914a-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="5914a-355">Transform- *позиционирование*</span><span class="sxs-lookup"><span data-stu-id="5914a-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="5914a-356">**X**</span><span class="sxs-lookup"><span data-stu-id="5914a-356">**X**</span></span> | <span data-ttu-id="5914a-357">**&**</span><span class="sxs-lookup"><span data-stu-id="5914a-357">**Y**</span></span>                  | <span data-ttu-id="5914a-358">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="5914a-358">**Z**</span></span> |
    | <span data-ttu-id="5914a-359">0</span><span class="sxs-lookup"><span data-stu-id="5914a-359">0</span></span>     | <span data-ttu-id="5914a-360">-1</span><span class="sxs-lookup"><span data-stu-id="5914a-360">-1</span></span>                     | <span data-ttu-id="5914a-361">0</span><span class="sxs-lookup"><span data-stu-id="5914a-361">0</span></span>     |


10. <span data-ttu-id="5914a-362">Щелкните **сферу** левой кнопкой мыши, чтобы выбрать ее.</span><span class="sxs-lookup"><span data-stu-id="5914a-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="5914a-363">На *панели инспектора* установите компонент *преобразования* со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="5914a-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="5914a-364">Transform- *позиционирование*</span><span class="sxs-lookup"><span data-stu-id="5914a-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="5914a-365">**X**</span><span class="sxs-lookup"><span data-stu-id="5914a-365">**X**</span></span> | <span data-ttu-id="5914a-366">**&**</span><span class="sxs-lookup"><span data-stu-id="5914a-366">**Y**</span></span>                  | <span data-ttu-id="5914a-367">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="5914a-367">**Z**</span></span> |
    | <span data-ttu-id="5914a-368">2</span><span class="sxs-lookup"><span data-stu-id="5914a-368">2</span></span>     | <span data-ttu-id="5914a-369">1</span><span class="sxs-lookup"><span data-stu-id="5914a-369">1</span></span>                      | <span data-ttu-id="5914a-370">2</span><span class="sxs-lookup"><span data-stu-id="5914a-370">2</span></span>     |

11. <span data-ttu-id="5914a-371">Щелкните **цилиндр** левой кнопкой мыши, чтобы выделить ее.</span><span class="sxs-lookup"><span data-stu-id="5914a-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="5914a-372">На *панели инспектора* установите компонент *преобразования* со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="5914a-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="5914a-373">Transform- *позиционирование*</span><span class="sxs-lookup"><span data-stu-id="5914a-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="5914a-374">**X**</span><span class="sxs-lookup"><span data-stu-id="5914a-374">**X**</span></span> | <span data-ttu-id="5914a-375">**&**</span><span class="sxs-lookup"><span data-stu-id="5914a-375">**Y**</span></span>                  | <span data-ttu-id="5914a-376">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="5914a-376">**Z**</span></span> |
    | <span data-ttu-id="5914a-377">-2</span><span class="sxs-lookup"><span data-stu-id="5914a-377">-2</span></span>    | <span data-ttu-id="5914a-378">1</span><span class="sxs-lookup"><span data-stu-id="5914a-378">1</span></span>                      | <span data-ttu-id="5914a-379">2</span><span class="sxs-lookup"><span data-stu-id="5914a-379">2</span></span>     |

12. <span data-ttu-id="5914a-380">Щелкните **куб** левой кнопкой мыши, чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="5914a-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="5914a-381">На *панели инспектора* установите компонент *преобразования* со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="5914a-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="5914a-382">Transform- *позиционирование*</span><span class="sxs-lookup"><span data-stu-id="5914a-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="5914a-383">*Поворот* преобразования</span><span class="sxs-lookup"><span data-stu-id="5914a-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="5914a-384">**X**</span><span class="sxs-lookup"><span data-stu-id="5914a-384">**X**</span></span> | <span data-ttu-id="5914a-385">**&**</span><span class="sxs-lookup"><span data-stu-id="5914a-385">**Y**</span></span>                   | <span data-ttu-id="5914a-386">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="5914a-386">**Z**</span></span> |  \| | <span data-ttu-id="5914a-387">**X**</span><span class="sxs-lookup"><span data-stu-id="5914a-387">**X**</span></span> | <span data-ttu-id="5914a-388">**&**</span><span class="sxs-lookup"><span data-stu-id="5914a-388">**Y**</span></span>                  | <span data-ttu-id="5914a-389">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="5914a-389">**Z**</span></span> |
    | <span data-ttu-id="5914a-390">0</span><span class="sxs-lookup"><span data-stu-id="5914a-390">0</span></span>     | <span data-ttu-id="5914a-391">1</span><span class="sxs-lookup"><span data-stu-id="5914a-391">1</span></span>                       | <span data-ttu-id="5914a-392">추가를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5914a-392">4</span></span>     |  \| | <span data-ttu-id="5914a-393">45</span><span class="sxs-lookup"><span data-stu-id="5914a-393">45</span></span>    | <span data-ttu-id="5914a-394">45</span><span class="sxs-lookup"><span data-stu-id="5914a-394">45</span></span>                     | <span data-ttu-id="5914a-395">0</span><span class="sxs-lookup"><span data-stu-id="5914a-395">0</span></span>     | 

13. <span data-ttu-id="5914a-396">Щелкните **новый текстовый** объект левой кнопкой мыши, чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="5914a-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="5914a-397">На *панели инспектора* установите компонент *преобразования* со следующими значениями:</span><span class="sxs-lookup"><span data-stu-id="5914a-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="5914a-398">Transform- *позиционирование*</span><span class="sxs-lookup"><span data-stu-id="5914a-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="5914a-399">Преобразование — *масштабирование*</span><span class="sxs-lookup"><span data-stu-id="5914a-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="5914a-400">**X**</span><span class="sxs-lookup"><span data-stu-id="5914a-400">**X**</span></span> | <span data-ttu-id="5914a-401">**&**</span><span class="sxs-lookup"><span data-stu-id="5914a-401">**Y**</span></span>                  | <span data-ttu-id="5914a-402">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="5914a-402">**Z**</span></span> |  \| | <span data-ttu-id="5914a-403">**X**</span><span class="sxs-lookup"><span data-stu-id="5914a-403">**X**</span></span> | <span data-ttu-id="5914a-404">**&**</span><span class="sxs-lookup"><span data-stu-id="5914a-404">**Y**</span></span>               | <span data-ttu-id="5914a-405">**Гармошкой**</span><span class="sxs-lookup"><span data-stu-id="5914a-405">**Z**</span></span> |
    | <span data-ttu-id="5914a-406">-2</span><span class="sxs-lookup"><span data-stu-id="5914a-406">-2</span></span>    | <span data-ttu-id="5914a-407">6</span><span class="sxs-lookup"><span data-stu-id="5914a-407">6</span></span>                      | <span data-ttu-id="5914a-408">9</span><span class="sxs-lookup"><span data-stu-id="5914a-408">9</span></span>     |  \| | <span data-ttu-id="5914a-409">0,1</span><span class="sxs-lookup"><span data-stu-id="5914a-409">0.1</span></span>   | <span data-ttu-id="5914a-410">0,1</span><span class="sxs-lookup"><span data-stu-id="5914a-410">0.1</span></span>                 | <span data-ttu-id="5914a-411">0,1</span><span class="sxs-lookup"><span data-stu-id="5914a-411">0.1</span></span>   | 

14. <span data-ttu-id="5914a-412">Измените **Размер шрифта** в компоненте **сетки текста** на **50**.</span><span class="sxs-lookup"><span data-stu-id="5914a-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="5914a-413">Измените *имя* объекта **сетки текста** на **текст диктовки**.</span><span class="sxs-lookup"><span data-stu-id="5914a-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![Создать трехмерный текстовый объект](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="5914a-415">Теперь структура панели иерархии должна выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5914a-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![сетка текста в представлении сцены](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="5914a-417">Окончательная сцена должна выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5914a-417">The final scene should look like the image below:</span></span>

    ![Представление сцены.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="5914a-419">Глава 5 — Создание класса Микрофонеманажер</span><span class="sxs-lookup"><span data-stu-id="5914a-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="5914a-420">Первым создаваемым сценарием является класс *микрофонеманажер* .</span><span class="sxs-lookup"><span data-stu-id="5914a-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="5914a-421">После этого вы создадите *луисманажер*, класс *поведений* и, наконец, класс *взгляда* (вы можете создать все эти данные сейчас, хотя он будет охватывать каждую главу).</span><span class="sxs-lookup"><span data-stu-id="5914a-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="5914a-422">Класс *микрофонеманажер* отвечает за:</span><span class="sxs-lookup"><span data-stu-id="5914a-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="5914a-423">Обнаружение устройства записи, подключенного к гарнитуре или компьютеру (в зависимости от того, какое значение используется по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="5914a-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="5914a-424">Запишите звук (голосовой) и используйте диктовку, чтобы сохранить ее в виде строки.</span><span class="sxs-lookup"><span data-stu-id="5914a-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="5914a-425">После приостановки голоса отправьте диктовку в класс *луисманажер* .</span><span class="sxs-lookup"><span data-stu-id="5914a-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="5914a-426">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="5914a-426">To create this class:</span></span> 

1.  <span data-ttu-id="5914a-427">Щелкните правой кнопкой мыши на *панели проект*, **Создайте папку >** .</span><span class="sxs-lookup"><span data-stu-id="5914a-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="5914a-428">Вызовите **скрипты**папки.</span><span class="sxs-lookup"><span data-stu-id="5914a-428">Call the folder **Scripts**.</span></span> 

    ![Создайте папку Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="5914a-430">После создания папки **Scripts (скрипты** ) дважды щелкните ее, чтобы открыть.</span><span class="sxs-lookup"><span data-stu-id="5914a-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="5914a-431">Затем в этой папке щелкните правой кнопкой мыши, **создайте > C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="5914a-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="5914a-432">Назовите сценарий *микрофонеманажер*.</span><span class="sxs-lookup"><span data-stu-id="5914a-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="5914a-433">Дважды щелкните *микрофонеманажер* , чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="5914a-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="5914a-434">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="5914a-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="5914a-435">Затем добавьте следующие переменные в класс *микрофонеманажер* :</span><span class="sxs-lookup"><span data-stu-id="5914a-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="5914a-436">Теперь необходимо добавить код для методов *"спящий" ()* и *"начало" ()* .</span><span class="sxs-lookup"><span data-stu-id="5914a-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="5914a-437">Они будут вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="5914a-437">These will be called when the class initializes:</span></span>

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
 
7.  <span data-ttu-id="5914a-438">Теперь вам нужен метод, который приложение использует для запуска и завершения записи речи, и передать его в класс *луисманажер* , который скоро будет создан.</span><span class="sxs-lookup"><span data-stu-id="5914a-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

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

8.  <span data-ttu-id="5914a-439">Добавьте *обработчик диктовки* , который будет вызываться при приостановке голоса.</span><span class="sxs-lookup"><span data-stu-id="5914a-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="5914a-440">Этот метод передаст текст диктовки в класс *луисманажер* .</span><span class="sxs-lookup"><span data-stu-id="5914a-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

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
    > <span data-ttu-id="5914a-441">Удалите метод *Update ()* , так как этот класс не будет его использовать.</span><span class="sxs-lookup"><span data-stu-id="5914a-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="5914a-442">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="5914a-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5914a-443">На этом этапе вы увидите ошибку на *панели консоли редактора Unity*.</span><span class="sxs-lookup"><span data-stu-id="5914a-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="5914a-444">Это обусловлено тем, что код ссылается на класс *луисманажер* , который будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="5914a-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="5914a-445">Глава 6 — создание класса Луисманажер</span><span class="sxs-lookup"><span data-stu-id="5914a-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="5914a-446">Пора создать класс *луисманажер* , который сделает вызов в службу Azure Luis.</span><span class="sxs-lookup"><span data-stu-id="5914a-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="5914a-447">Этот класс предназначен для получения текста диктовки от класса *микрофонеманажер* и отправки его в *API распознавания речи Azure* для анализа.</span><span class="sxs-lookup"><span data-stu-id="5914a-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="5914a-448">Этот класс будет десериализовать ответ *JSON* и вызвать соответствующие методы класса *поведений* , чтобы активировать действие.</span><span class="sxs-lookup"><span data-stu-id="5914a-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="5914a-449">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="5914a-449">To create this class:</span></span> 

1.  <span data-ttu-id="5914a-450">Дважды щелкните папку **Scripts** , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="5914a-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="5914a-451">Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать C# > скрипт**.</span><span class="sxs-lookup"><span data-stu-id="5914a-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="5914a-452">Назовите сценарий *луисманажер*.</span><span class="sxs-lookup"><span data-stu-id="5914a-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="5914a-453">Дважды щелкните скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5914a-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="5914a-454">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="5914a-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="5914a-455">Начнем с создания трех классов **внутри** класса *луисманажер* (в рамках одного файла скрипта выше метода *Start ()* ), который будет представлять Десериализованный ответ JSON из Azure.</span><span class="sxs-lookup"><span data-stu-id="5914a-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

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

6.  <span data-ttu-id="5914a-456">Затем добавьте следующие переменные в класс *луисманажер* :</span><span class="sxs-lookup"><span data-stu-id="5914a-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="5914a-457">Обязательно поместите конечную точку LUIS в сейчас (которая получится на портале LUIS).</span><span class="sxs-lookup"><span data-stu-id="5914a-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="5914a-458">Теперь необходимо добавить код для метода " *спящий ()* ".</span><span class="sxs-lookup"><span data-stu-id="5914a-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="5914a-459">Этот метод будет вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="5914a-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="5914a-460">Теперь вам потребуются методы, которые приложение использует для отправки диктовки, полученной от класса *микрофонеманажер* , в *Luis*, а затем получения и десериализации ответа.</span><span class="sxs-lookup"><span data-stu-id="5914a-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="5914a-461">После определения цели и связанных сущностей они передаются в экземпляр класса *поведений* , чтобы активировать предполагаемое действие.</span><span class="sxs-lookup"><span data-stu-id="5914a-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

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
 
11. <span data-ttu-id="5914a-462">Создайте новый метод с именем *аналисереспонсилементс ()* , который будет считывать результирующий *Аналиседкуери* и определять сущности.</span><span class="sxs-lookup"><span data-stu-id="5914a-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="5914a-463">После определения этих сущностей они будут переданы в экземпляр класса *поведений* для использования в действиях.</span><span class="sxs-lookup"><span data-stu-id="5914a-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

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

            // Depending on the topmost recognized intent, read the entities name
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
    > <span data-ttu-id="5914a-464">Удалите методы *Start ()* и *Update ()* , так как этот класс не будет использовать их.</span><span class="sxs-lookup"><span data-stu-id="5914a-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="5914a-465">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="5914a-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="5914a-466">На этом этапе вы увидите несколько ошибок на *панели консоли редактора Unity*.</span><span class="sxs-lookup"><span data-stu-id="5914a-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="5914a-467">Это обусловлено тем, что код ссылается на класс *поведения* , который будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="5914a-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="5914a-468">Глава 7 — создание класса поведения</span><span class="sxs-lookup"><span data-stu-id="5914a-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="5914a-469">Класс *поведений* активирует действия с помощью сущностей, предоставляемых классом *луисманажер* .</span><span class="sxs-lookup"><span data-stu-id="5914a-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="5914a-470">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="5914a-470">To create this class:</span></span> 

1.  <span data-ttu-id="5914a-471">Дважды щелкните папку **Scripts** , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="5914a-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="5914a-472">Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать C# > скрипт**.</span><span class="sxs-lookup"><span data-stu-id="5914a-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="5914a-473">Назовите *поведение*сценария.</span><span class="sxs-lookup"><span data-stu-id="5914a-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="5914a-474">Дважды щелкните скрипт, чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="5914a-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="5914a-475">Затем добавьте следующие переменные в класс *поведения* :</span><span class="sxs-lookup"><span data-stu-id="5914a-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="5914a-476">Добавьте код метода " *спящий ()* ".</span><span class="sxs-lookup"><span data-stu-id="5914a-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="5914a-477">Этот метод будет вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="5914a-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="5914a-478">Следующие методы вызываются классом *луисманажер* (который был создан ранее), чтобы определить, какой объект является целевым объектом запроса, и затем активировать соответствующее действие.</span><span class="sxs-lookup"><span data-stu-id="5914a-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

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
 
7.  <span data-ttu-id="5914a-479">Добавьте метод *финдтаржет ()* , чтобы определить, какой из *объекты gameobject* является целевым объектом текущей цели.</span><span class="sxs-lookup"><span data-stu-id="5914a-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="5914a-480">Этот метод по умолчанию имеет значение "газед" для целевого объекта *GameObject* , если в сущностях не определена явная цель.</span><span class="sxs-lookup"><span data-stu-id="5914a-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
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
    > <span data-ttu-id="5914a-481">Удалите методы *Start ()* и *Update ()* , так как этот класс не будет использовать их.</span><span class="sxs-lookup"><span data-stu-id="5914a-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="5914a-482">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="5914a-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="5914a-483">Глава 8 — Создание класса «взгляд»</span><span class="sxs-lookup"><span data-stu-id="5914a-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="5914a-484">Последним классом, который потребуется для завершения этого приложения, является класс « *взгляд* ».</span><span class="sxs-lookup"><span data-stu-id="5914a-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="5914a-485">Этот класс обновляет ссылку на *GameObject* в данный момент в визуальном фокусе пользователя.</span><span class="sxs-lookup"><span data-stu-id="5914a-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="5914a-486">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="5914a-486">To create this Class:</span></span> 

1.  <span data-ttu-id="5914a-487">Дважды щелкните папку **Scripts** , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="5914a-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="5914a-488">Щелкните правой кнопкой мыши в папке **Scripts** и выберите **создать C# > скрипт**.</span><span class="sxs-lookup"><span data-stu-id="5914a-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="5914a-489">Присвойте скрипту имя « *взгляд*».</span><span class="sxs-lookup"><span data-stu-id="5914a-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="5914a-490">Дважды щелкните скрипт, чтобы открыть его в *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="5914a-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="5914a-491">Вставьте следующий код для этого класса:</span><span class="sxs-lookup"><span data-stu-id="5914a-491">Insert the following code for this class:</span></span>

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
 
5.  <span data-ttu-id="5914a-492">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="5914a-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="5914a-493">Глава 9 — завершение настройки сцены</span><span class="sxs-lookup"><span data-stu-id="5914a-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="5914a-494">Чтобы завершить настройку сцены, перетащите каждый созданный скрипт из папки сценарии в **основной объект Camera** на *панели Иерархия*.</span><span class="sxs-lookup"><span data-stu-id="5914a-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="5914a-495">Выберите **основную камеру** и взгляните на *Панель инспектора*, вы сможете увидеть каждый присоединенный сценарий, и вы заметите, что в каждом скрипте есть параметры, которые еще не заданы.</span><span class="sxs-lookup"><span data-stu-id="5914a-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![Настройка целевых объектов для ссылок на камеру.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="5914a-497">Чтобы правильно задать эти параметры, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="5914a-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="5914a-498">*Микрофонеманажер*:</span><span class="sxs-lookup"><span data-stu-id="5914a-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="5914a-499">На *панели Иерархия*перетащите текстовый объект **диктовки** в поле значение **текстового параметра диктовки** .</span><span class="sxs-lookup"><span data-stu-id="5914a-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="5914a-500">*Поведение*на *панели Иерархия*:</span><span class="sxs-lookup"><span data-stu-id="5914a-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="5914a-501">Перетащите объект **Sphere** в поле Целевая ссылка на *сферу* .</span><span class="sxs-lookup"><span data-stu-id="5914a-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="5914a-502">Перетащите **цилиндр** в поле Целевая ссылка *цилиндра* .</span><span class="sxs-lookup"><span data-stu-id="5914a-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="5914a-503">Перетащите **куб** в поле Целевая ссылка на *куб* .</span><span class="sxs-lookup"><span data-stu-id="5914a-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="5914a-504">*Взгляните*:</span><span class="sxs-lookup"><span data-stu-id="5914a-504">*Gaze*:</span></span>

        - <span data-ttu-id="5914a-505">Установите *Максимальное расстояние от взгляда* до **300** (если оно еще не указано).</span><span class="sxs-lookup"><span data-stu-id="5914a-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="5914a-506">Результат должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="5914a-506">The result should look like the image below:</span></span>

    ![Показаны целевые объекты для ссылок на камеру, теперь задано.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="5914a-508">Глава 10 — тестирование в редакторе Unity</span><span class="sxs-lookup"><span data-stu-id="5914a-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="5914a-509">Проверьте, правильно ли реализована Настройка сцены.</span><span class="sxs-lookup"><span data-stu-id="5914a-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="5914a-510">Убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="5914a-510">Ensure that:</span></span>

-   <span data-ttu-id="5914a-511">Все скрипты присоединяются к **главному объекту Camera** .</span><span class="sxs-lookup"><span data-stu-id="5914a-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="5914a-512">Все поля на *панели инспектора основной камеры* назначены должным образом.</span><span class="sxs-lookup"><span data-stu-id="5914a-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="5914a-513">Нажмите кнопку **воспроизвести** в *редакторе Unity*.</span><span class="sxs-lookup"><span data-stu-id="5914a-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="5914a-514">Приложение должно выполняться в присоединенной иммерсивного гарнитуре.</span><span class="sxs-lookup"><span data-stu-id="5914a-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="5914a-515">Попробуйте несколько фразы продолжительностью, например:</span><span class="sxs-lookup"><span data-stu-id="5914a-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="5914a-516">Если в консоли Unity появляется сообщение об ошибке о смене звукового устройства по умолчанию, возможно, сцена не работает должным образом.</span><span class="sxs-lookup"><span data-stu-id="5914a-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="5914a-517">Это связано с тем, как портал смешанной реальности работает со встроенными микротелефонами для гарнитур, имеющих их.</span><span class="sxs-lookup"><span data-stu-id="5914a-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="5914a-518">Если вы видите эту ошибку, просто закройте сцену и снова запустите ее, и она должна работать должным образом.</span><span class="sxs-lookup"><span data-stu-id="5914a-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="5914a-519">Глава 11 — Создание и загружать неопубликованные решения UWP</span><span class="sxs-lookup"><span data-stu-id="5914a-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="5914a-520">После проверки того, что приложение работает в редакторе Unity, можно приступать к сборке и развертыванию.</span><span class="sxs-lookup"><span data-stu-id="5914a-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="5914a-521">Для сборки:</span><span class="sxs-lookup"><span data-stu-id="5914a-521">To Build:</span></span>

1.  <span data-ttu-id="5914a-522">Сохраните текущую сцену, щелкнув **файл > сохранить**.</span><span class="sxs-lookup"><span data-stu-id="5914a-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="5914a-523">Выберите **файл > параметры сборки**.</span><span class="sxs-lookup"><span data-stu-id="5914a-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="5914a-524">Установите флажок " **проекты Unity C#**  " (удобно для просмотра и отладки кода после создания проекта UWP.</span><span class="sxs-lookup"><span data-stu-id="5914a-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="5914a-525">Щелкните **Добавить открытые сцены**, а затем — **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="5914a-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Окно "параметры сборки"](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="5914a-527">Вам будет предложено выбрать папку, в которой нужно построить решение.</span><span class="sxs-lookup"><span data-stu-id="5914a-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="5914a-528">Создайте папку *Builds* и в этой папке создайте другую папку с соответствующим именем по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="5914a-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="5914a-529">Щелкните **выбрать папку** , чтобы начать сборку в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="5914a-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="5914a-530">![создать папку сборок](images/AzureLabs-Lab3-44.png)
    ![выберите папку сборок](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="5914a-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="5914a-531">После завершения сборки Unity (может занять некоторое время) он должен открыть окно **проводника** в расположении сборки.</span><span class="sxs-lookup"><span data-stu-id="5914a-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="5914a-532">Для развертывания на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="5914a-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="5914a-533">В *Visual Studio*откройте файл решения, который был создан в [предыдущей главе](#chapter-10--test-in-the-unity-editor).</span><span class="sxs-lookup"><span data-stu-id="5914a-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="5914a-534">На **платформе решения**выберите **x86**, **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="5914a-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="5914a-535">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="5914a-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="5914a-536">Для Microsoft HoloLens может быть проще установить этот параметр на *Удаленный компьютер*, чтобы вы не были подключены к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="5914a-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="5914a-537">Однако необходимо также выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="5914a-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="5914a-538">Определите **IP-адрес** HoloLens, который можно найти в *параметрах > сети & Интернет > Wi-Fi > Дополнительные параметры*. IPv4 — это адрес, который следует использовать.</span><span class="sxs-lookup"><span data-stu-id="5914a-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="5914a-539">Убедитесь, **что включен** **режим разработчика** ; находится в *параметрах > Update & > безопасности для разработчиков*.</span><span class="sxs-lookup"><span data-stu-id="5914a-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Развертывание приложения](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="5914a-541">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение** ", чтобы загружать неопубликованные приложение на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5914a-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="5914a-542">Теперь приложение должно отобразиться в списке установленных приложений, готовых к запуску.</span><span class="sxs-lookup"><span data-stu-id="5914a-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="5914a-543">После запуска приложение предложит авторизовать доступ к _микрофону_.</span><span class="sxs-lookup"><span data-stu-id="5914a-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="5914a-544">Используйте *контроллеры движения*, *Ввод голоса*или *клавиатуру* , чтобы нажать кнопку **Да** .</span><span class="sxs-lookup"><span data-stu-id="5914a-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="5914a-545">Глава 12 — улучшение службы LUIS</span><span class="sxs-lookup"><span data-stu-id="5914a-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="5914a-546">Эта глава чрезвычайно важна и, возможно, потребуется выполнить итерацию несколько раз, так как она поможет улучшить точность службы LUIS: Убедитесь, что вы выполнили это действие.</span><span class="sxs-lookup"><span data-stu-id="5914a-546">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="5914a-547">Чтобы улучшить уровень понимания, предоставляемый LUIS, необходимо захватить новый фразы продолжительностью и использовать их для повторного обучения приложения LUIS.</span><span class="sxs-lookup"><span data-stu-id="5914a-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="5914a-548">Например, вы могли обучить LUIS, чтобы понять "увеличение" и "размер", но не хотите, чтобы ваше приложение также понимало такие слова, как "увеличить"?</span><span class="sxs-lookup"><span data-stu-id="5914a-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="5914a-549">Когда вы будете использовать приложение несколько раз, все, что вы сказали, будет собрано LUIS и доступным на ПОРТАЛе LUIS.</span><span class="sxs-lookup"><span data-stu-id="5914a-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="5914a-550">Перейдите в приложение портала, следуя этой [ссылке](https://www.luis.ai/home), и выполните вход.</span><span class="sxs-lookup"><span data-stu-id="5914a-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="5914a-551">Войдя с учетными данными MS, щелкните *имя своего приложения*.</span><span class="sxs-lookup"><span data-stu-id="5914a-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="5914a-552">Нажмите кнопку **проверить конечную точку фразы продолжительностью** в левой части страницы.</span><span class="sxs-lookup"><span data-stu-id="5914a-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Проверка фразы продолжительностью](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="5914a-554">Вы увидите список фразы продолжительностью, отправленных в LUIS приложением Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5914a-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Список фразы продолжительностью](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="5914a-556">Вы увидите некоторые выделенные *сущности*.</span><span class="sxs-lookup"><span data-stu-id="5914a-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="5914a-557">Наведя указатель мыши на каждое выделенное слово, вы можете ознакомиться с каждым из utterance и определить, какая сущность распознана правильно, какие сущности являются неправильными и какие сущности пропущены.</span><span class="sxs-lookup"><span data-stu-id="5914a-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="5914a-558">В приведенном выше примере было обнаружено, что слово «Спиар» было выделено в качестве целевого объекта, поэтому необходимо исправить ошибку. это можно сделать, наведя указатель мыши на слово и выбрав пункт **Удалить метку**.</span><span class="sxs-lookup"><span data-stu-id="5914a-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="5914a-559">![проверить фразы продолжительностью](images/AzureLabs-Lab3-49.png)
![удалить метку Image](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="5914a-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="5914a-560">Если обнаружены неправильные фразы продолжительностью, их можно удалить с помощью кнопки **Удалить** в правой части экрана.</span><span class="sxs-lookup"><span data-stu-id="5914a-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Удалить неправильный фразы продолжительностью](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="5914a-562">Или, если вы считаете, что LUIS правильно интерпретирует utterance, можно проверить его понимание с помощью кнопки **Добавить в соответствие** .</span><span class="sxs-lookup"><span data-stu-id="5914a-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Добавить в согласованное назначение](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="5914a-564">После сортировки всех отображаемых фразы продолжительностью попробуйте перезагрузить страницу, чтобы узнать, доступны ли другие.</span><span class="sxs-lookup"><span data-stu-id="5914a-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="5914a-565">Очень важно повторить этот процесс столько раз, сколько возможно, чтобы улучшить понимание приложения.</span><span class="sxs-lookup"><span data-stu-id="5914a-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="5914a-566">**Веселитесь!**</span><span class="sxs-lookup"><span data-stu-id="5914a-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="5914a-567">Готовое интегрированное приложение LUIS</span><span class="sxs-lookup"><span data-stu-id="5914a-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="5914a-568">Поздравляем! вы создали приложение смешанной реальности, которое использует службу Azure Language Understanding Intelligence, чтобы понять, что говорит пользователь, и действовать над этими сведениями.</span><span class="sxs-lookup"><span data-stu-id="5914a-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![результат лаборатории](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="5914a-570">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="5914a-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="5914a-571">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="5914a-571">Exercise 1</span></span>

<span data-ttu-id="5914a-572">При использовании этого приложения вы можете заметить, что если взглянуть на объект Floor и попросить изменить его цвет, это сделает это.</span><span class="sxs-lookup"><span data-stu-id="5914a-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="5914a-573">Можно ли узнать, как запретить приложению изменять цвет этажа?</span><span class="sxs-lookup"><span data-stu-id="5914a-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="5914a-574">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="5914a-574">Exercise 2</span></span>

<span data-ttu-id="5914a-575">Попробуйте расширить возможности LUIS и приложений, добавив дополнительные функции для объектов в сцене. в качестве примера можно создать новые объекты в точке попадания, в зависимости от того, что сообщает пользователь, а затем использовать эти объекты вместе с текущими объектами сцены с помощью существующих команд.</span><span class="sxs-lookup"><span data-stu-id="5914a-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
