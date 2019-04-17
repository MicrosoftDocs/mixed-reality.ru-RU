---
title: Г-н и 301 Azure - перевода
description: Выполните этот курс, чтобы узнать, как реализовать Translator Text API Azure в приложениях смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, translator text API, hololens, создающий эффект присутствия, виртуальной реальности
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603608"
---
>[!NOTE]
><span data-ttu-id="81b0b-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="81b0b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="81b0b-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="81b0b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="81b0b-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="81b0b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="81b0b-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="81b0b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="81b0b-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="81b0b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="81b0b-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="81b0b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="81b0b-110">Г-н и Azure 301: систем перевода.</span><span class="sxs-lookup"><span data-stu-id="81b0b-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="81b0b-111">В рамках этого курса вы узнаете, как добавить возможности перевода приложений в смешанной реальности, с помощью Azure Cognitive Services, с помощью API перевода текстов.</span><span class="sxs-lookup"><span data-stu-id="81b0b-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Конечный продукт](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="81b0b-113">API перевода текстов — перевод службы, который работает в практически в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="81b0b-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="81b0b-114">Службы облачных, и, с помощью вызова REST API, приложение можно сделать использовать технологии нейронный машинный перевод, перевод текста на другой язык.</span><span class="sxs-lookup"><span data-stu-id="81b0b-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="81b0b-115">Дополнительные сведения см. в статье [страницы API перевода текстов Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="81b0b-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="81b0b-116">По завершении этого курса вы получите с приложением смешанной реальности, которое будет осуществлять следующее:</span><span class="sxs-lookup"><span data-stu-id="81b0b-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="81b0b-117">Пользователь будет говорите в микрофон, подключенный к иммерсивных Гарнитура (VR) (или встроенный микрофон HoloLens).</span><span class="sxs-lookup"><span data-stu-id="81b0b-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="81b0b-118">Приложение будет захвата диктовка и отправить его на API перевода текстов Azure.</span><span class="sxs-lookup"><span data-stu-id="81b0b-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="81b0b-119">Результат перевода будет отображаться в группе простой пользовательский Интерфейс в сцене Unity.</span><span class="sxs-lookup"><span data-stu-id="81b0b-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="81b0b-120">Этот курс ознакомят вас для получения результатов от службы перевода в приложение на базе Unity образец.</span><span class="sxs-lookup"><span data-stu-id="81b0b-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="81b0b-121">Это будет необходимо применение этих понятий в пользовательское приложение, возможно, вы разрабатываете.</span><span class="sxs-lookup"><span data-stu-id="81b0b-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="81b0b-122">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="81b0b-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="81b0b-123">Курс</span><span class="sxs-lookup"><span data-stu-id="81b0b-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="81b0b-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="81b0b-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="81b0b-125"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="81b0b-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="81b0b-126">Г-н и Azure 301: систем перевода.</span><span class="sxs-lookup"><span data-stu-id="81b0b-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="81b0b-127">✔️</span><span class="sxs-lookup"><span data-stu-id="81b0b-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="81b0b-128">✔️</span><span class="sxs-lookup"><span data-stu-id="81b0b-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="81b0b-129">Хотя этот курс основное внимание уделяется Windows Mixed Reality иммерсивную (VR), можно также применить полученные знания в этом курсе для Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="81b0b-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="81b0b-130">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="81b0b-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="81b0b-131">При использовании HoloLens, вы можете заметить некоторые echo во время записи голоса.</span><span class="sxs-lookup"><span data-stu-id="81b0b-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="81b0b-132">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="81b0b-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="81b0b-133">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="81b0b-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="81b0b-134">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (мая 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="81b0b-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="81b0b-135">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием что можно найти в новой версии по сравнению приведенных ниже .</span><span class="sxs-lookup"><span data-stu-id="81b0b-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="81b0b-136">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="81b0b-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="81b0b-137">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="81b0b-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="81b0b-138">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="81b0b-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="81b0b-139">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="81b0b-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="81b0b-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="81b0b-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="81b0b-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="81b0b-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="81b0b-142">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="81b0b-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="81b0b-143">Наушники с помощью встроенного микрофона (если гарнитура отсутствует встроенный mic, а также докладчиков)</span><span class="sxs-lookup"><span data-stu-id="81b0b-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="81b0b-144">Доступ к Интернету для Azure установки и перевода извлечения</span><span class="sxs-lookup"><span data-stu-id="81b0b-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="81b0b-145">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="81b0b-145">Before you start</span></span>

- <span data-ttu-id="81b0b-146">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="81b0b-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="81b0b-147">Код в этом руководстве, позволит вам для записи с микрофона устройства по умолчанию, подключенном к ПК.</span><span class="sxs-lookup"><span data-stu-id="81b0b-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="81b0b-148">Убедитесь, что на устройстве "микрофон" по умолчанию имеет значение устройству, которое планируется использовать для записи голоса.</span><span class="sxs-lookup"><span data-stu-id="81b0b-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="81b0b-149">Чтобы разрешить Систему, чтобы включить режим диктовки, перейдите в раздел **параметры > о конфиденциальности > речи, рукописного ввода и введя** и нажмите кнопку **Включение службы распознавания речи и ввода предложения**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="81b0b-150">При использовании микрофон и наушники – (или встроен) вашего гарнитуры, убедитесь, что параметр «После я wear Мой гарнитуры, перейдите на mic гарнитура» включена в **параметры > смешанной реальности > аудио- и речи**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Параметры смешанной реальности](images/AzureLabs-Lab1-00-5.png)

   ![Параметр "микрофон"](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="81b0b-153">Имейте в виду, что при разработке для иммерсивных гарнитура, для этой лабораторной работы, возможно возникновение проблем звуковые выходные данные на устройстве.</span><span class="sxs-lookup"><span data-stu-id="81b0b-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="81b0b-154">Это из-за проблемы с Unity, в котором исправлена в более поздних версиях Unity (Unity 2018.2).</span><span class="sxs-lookup"><span data-stu-id="81b0b-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="81b0b-155">Проблема не позволяет изменять на устройстве звуковые выходные данные по умолчанию во время выполнения Unity.</span><span class="sxs-lookup"><span data-stu-id="81b0b-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="81b0b-156">Решения убедитесь, что выполнены описанные выше действия и закройте и снова откройте редактор, если эта проблема проявляется.</span><span class="sxs-lookup"><span data-stu-id="81b0b-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="81b0b-157">Глава 1 – портала Azure</span><span class="sxs-lookup"><span data-stu-id="81b0b-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="81b0b-158">Чтобы использовать Azure Translator API, необходимо настроить экземпляр службы, чтобы сделать доступными для приложения.</span><span class="sxs-lookup"><span data-stu-id="81b0b-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="81b0b-159">Войдите в [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="81b0b-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="81b0b-160">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="81b0b-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="81b0b-161">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="81b0b-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="81b0b-162">После входа в систему щелкните **New** в верхнем левом углу и выполните поиск «Translator Text API».</span><span class="sxs-lookup"><span data-stu-id="81b0b-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="81b0b-163">Выберите **введите**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-163">Select **Enter**.</span></span>

    ![Новый ресурс](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="81b0b-165">Слово **New** может были заменены **создать ресурс**, в новых порталов.</span><span class="sxs-lookup"><span data-stu-id="81b0b-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="81b0b-166">Новая страница будет предоставить описание *API перевода текстов* службы.</span><span class="sxs-lookup"><span data-stu-id="81b0b-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="81b0b-167">В нижней левой части этой страницы выберите **создать** кнопку, чтобы создать ассоциацию с данным службы.</span><span class="sxs-lookup"><span data-stu-id="81b0b-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Создание Translator Text API службы](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="81b0b-169">Когда вы перейдете на **создать**:</span><span class="sxs-lookup"><span data-stu-id="81b0b-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="81b0b-170">Вставить нужный **имя** для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="81b0b-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="81b0b-171">Выберите соответствующее **подписки**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="81b0b-172">Выберите **Ценовая** подходит для вас, если это первое времени на создание *Translator текстовая служба*, уровень "бесплатный" (с именем F0) должны быть доступны для вас.</span><span class="sxs-lookup"><span data-stu-id="81b0b-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="81b0b-173">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="81b0b-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="81b0b-174">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="81b0b-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="81b0b-175">Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как многому) в группе общих ресурсов).</span><span class="sxs-lookup"><span data-stu-id="81b0b-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="81b0b-176">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, пожалуйста, [откройте статью группы ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="81b0b-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="81b0b-177">Определить **расположение** для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="81b0b-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="81b0b-178">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="81b0b-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="81b0b-179">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="81b0b-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="81b0b-180">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="81b0b-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="81b0b-181">Щелкните **Создать**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-181">Select **Create**.</span></span>

        ![Нажмите кнопку "Создать".](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="81b0b-183">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="81b0b-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="81b0b-184">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="81b0b-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Azure уведомление о создании службы](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="81b0b-186">Щелкните уведомление, чтобы изучить ваш новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="81b0b-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Перейдите к всплывающее окно ресурсов.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="81b0b-188">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="81b0b-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="81b0b-189">Откроется в новом экземпляре Translator Text API службы.</span><span class="sxs-lookup"><span data-stu-id="81b0b-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Страница службы API текст перевода](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="81b0b-191">В этом руководстве описано приложение должно выполнять вызовы в службу, которая осуществляется с помощью ключа подписки вашей службы.</span><span class="sxs-lookup"><span data-stu-id="81b0b-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="81b0b-192">Из *быстрого запуска* странице вашего *Translator Text* службы, перейдите к первому шагу *получите ключи*и нажмите кнопку **ключи** (вы можете также выполнить эту операцию, щелкнув синий гиперссылки ключи, расположенный в меню навигации служб, обозначенное с помощью значок ключа).</span><span class="sxs-lookup"><span data-stu-id="81b0b-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="81b0b-193">Это позволит службе *ключи*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="81b0b-194">Сделайте копию один из отображаемых разделов, так как он потребуется позже в проекте.</span><span class="sxs-lookup"><span data-stu-id="81b0b-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="81b0b-195">Глава 2 – Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="81b0b-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="81b0b-196">Настроить и проверить ваш иммерсивных гарнитуры смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="81b0b-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="81b0b-197">Вам не потребуется контроллеры движения курс с демороликами.</span><span class="sxs-lookup"><span data-stu-id="81b0b-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="81b0b-198">Если вам требуется поддерживает настройку иммерсивных гарнитура, [выполните следующие действия](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="81b0b-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="81b0b-199">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов:</span><span class="sxs-lookup"><span data-stu-id="81b0b-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="81b0b-200">Откройте *Unity* и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-200">Open *Unity* and click **New**.</span></span> 

    ![Начните новый проект Unity.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="81b0b-202">Теперь необходимо будет указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="81b0b-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="81b0b-203">Вставить **MR_Translation**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="81b0b-204">Убедитесь, что тип проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="81b0b-205">Задайте *расположение* в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="81b0b-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="81b0b-206">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-206">Then, click **Create project**.</span></span>

    ![Укажите сведения для нового проекта Unity.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="81b0b-208">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="81b0b-209">Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="81b0b-210">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="81b0b-211">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="81b0b-211">Close the **Preferences** window.</span></span>

    ![Обновите настройки редактора скриптов.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="81b0b-213">Перейдите к **файл > Параметры сборки** и переключитесь на платформе, которое **универсальной платформы Windows**, щелкнув **переключения платформы** кнопки.</span><span class="sxs-lookup"><span data-stu-id="81b0b-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Создавайте окно "Параметры", переключить платформу для универсальной платформы Windows.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="81b0b-215">Перейдите к **файл > Параметры сборки** и убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="81b0b-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="81b0b-216">**Целевое устройство** присваивается **любого устройства**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="81b0b-217">Microsoft HoloLens, задайте **целевое устройство** для *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="81b0b-218">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="81b0b-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="81b0b-219">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="81b0b-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="81b0b-220">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="81b0b-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="81b0b-221">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="81b0b-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="81b0b-222">Сохраните сцены и добавить его к сборке.</span><span class="sxs-lookup"><span data-stu-id="81b0b-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="81b0b-223">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="81b0b-224">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="81b0b-224">A save window will appear.</span></span>

            ![Нажмите кнопку Добавить кнопку open сцены](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="81b0b-226">Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Создание новой папки scripts](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="81b0b-228">Откройте только что созданный **сцены** папку, а затем в *имя файла*: текстовое поле, тип **MR_TranslationScene**, нажмите клавишу **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Присвойте имя новой сцены.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="81b0b-230">Следует помнить, что необходимо сохранить в Unity кадром *активы* папку, так как они должны быть связаны с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="81b0b-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="81b0b-231">Создание папки сцены (и другие аналогичные папки) — это типичный способ структурирования проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="81b0b-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="81b0b-232">Для остальных параметров, в *параметры построения*, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="81b0b-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="81b0b-233">В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится.</span><span class="sxs-lookup"><span data-stu-id="81b0b-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Открытие параметров проигрывателя.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="81b0b-235">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="81b0b-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="81b0b-236">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="81b0b-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="81b0b-237">**Версия среды выполнения сценариев** должно быть **стабильной** (.NET 3.5 эквивалент).</span><span class="sxs-lookup"><span data-stu-id="81b0b-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="81b0b-238">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="81b0b-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="81b0b-239">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="81b0b-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Обновите другие параметры.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="81b0b-241">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="81b0b-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="81b0b-242">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="81b0b-242">**InternetClient**</span></span>
        2. <span data-ttu-id="81b0b-243">**"Микрофон"**</span><span class="sxs-lookup"><span data-stu-id="81b0b-243">**Microphone**</span></span>

            ![Обновление параметров публикации.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="81b0b-245">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.</span><span class="sxs-lookup"><span data-stu-id="81b0b-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Обновление параметров R X.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="81b0b-247">Вернитесь в **параметры построения**, *Unity C# проекты* больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="81b0b-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="81b0b-248">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="81b0b-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="81b0b-249">Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="81b0b-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="81b0b-250">Глава 3 — Настройка Main Camera</span><span class="sxs-lookup"><span data-stu-id="81b0b-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81b0b-251">Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете [загрузить этот .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), импортировать его в проект в качестве [ *Пользовательского пакета*](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 5](#chapter-5--create-the-results-class).</span><span class="sxs-lookup"><span data-stu-id="81b0b-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="81b0b-252">По-прежнему необходимо будет создать проект Unity.</span><span class="sxs-lookup"><span data-stu-id="81b0b-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="81b0b-253">В *панели иерархии*, вы найдете объект с именем **Main Camera**, этот объект представляет вашей точки зрения «head» приложения «в».</span><span class="sxs-lookup"><span data-stu-id="81b0b-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="81b0b-254">С помощью панели мониторинга Unity перед глазами, выберите **GameObject камеры Main**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="81b0b-255">Можно будет заметить, что *панели Инспектора* (обычно находится в правой части панели мониторинга) будут отображаться различные компоненты, *GameObject*, с помощью *преобразования* в верхней, за которым следует *камеры*и некоторые другие компоненты.</span><span class="sxs-lookup"><span data-stu-id="81b0b-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="81b0b-256">Необходимо будет сбросить преобразование объекта Main Camera, поэтому расположено верно.</span><span class="sxs-lookup"><span data-stu-id="81b0b-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="81b0b-257">Чтобы сделать это, выберите **шестеренки** значок рядом с камеры *преобразования* компонента, а затем выбрав **сбросить**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Сбросьте преобразование Main Camera.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="81b0b-259">*Преобразования* компонент должен выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="81b0b-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="81b0b-260">*Позиции* присваивается **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="81b0b-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="81b0b-261">*Поворот* присваивается **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="81b0b-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="81b0b-262">И *масштабирования* присваивается **1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="81b0b-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Преобразование информации для камеры](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="81b0b-264">Далее с помощью **Main Camera** объекта выбран, см. в разделе **добавить компонент** расположенную в нижней части *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="81b0b-265">Выберите эту кнопку и поиск (либо путем ввода *источника аудио* в поле поиска или перехода в разделах) для компонента, который вызывается **источника аудио** как показано ниже и выберите его (нажмите клавишу ВВОД на нем Кроме того, работает).</span><span class="sxs-lookup"><span data-stu-id="81b0b-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="81b0b-266">*Источника аудио* добавляется компонент **Main Camera**, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="81b0b-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Добавление компонента источника аудио.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="81b0b-268">Для Microsoft HoloLens, необходимо также изменить следующим образом, являются частью **камеры** компонентом вашего **Main Camera**:</span><span class="sxs-lookup"><span data-stu-id="81b0b-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="81b0b-269">**Очистите флаги:** Сплошным цветом.</span><span class="sxs-lookup"><span data-stu-id="81b0b-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="81b0b-270">**Фон** "черная, альфа-канал 0" — Hex цвет: #00000000.</span><span class="sxs-lookup"><span data-stu-id="81b0b-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="81b0b-271">Глава 4 – холст отладки программы установки</span><span class="sxs-lookup"><span data-stu-id="81b0b-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="81b0b-272">Чтобы отобразить вход и выход преобразования, необходимо создать основной пользовательский Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="81b0b-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="81b0b-273">Для этого курса вы создадите объект Canvas пользовательского интерфейса с несколькими объектами «Text» для отображения данных.</span><span class="sxs-lookup"><span data-stu-id="81b0b-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="81b0b-274">Щелкните правой кнопкой мыши пустую часть области *панели иерархии*в разделе **пользовательского интерфейса**, добавьте **холст**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Добавьте новый объект Canvas пользовательского интерфейса.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="81b0b-276">Холст объект выбран, в *панели Инспектора* (в компоненте «Canvas»), измените **режим рендеринга** для **мировом пространстве**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="81b0b-277">Затем измените следующие параметры в *панели Инспектора Rect преобразования*:</span><span class="sxs-lookup"><span data-stu-id="81b0b-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="81b0b-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="81b0b-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="81b0b-279">*Ширина* - 500</span><span class="sxs-lookup"><span data-stu-id="81b0b-279">*Width* -    500</span></span>
    3. <span data-ttu-id="81b0b-280">*Высота* - 300</span><span class="sxs-lookup"><span data-stu-id="81b0b-280">*Height* -   300</span></span>
    4. <span data-ttu-id="81b0b-281">*Масштаб* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="81b0b-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Обновление преобразования rect полотна.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="81b0b-283">Щелкните правой кнопкой мыши **холст** в *панели иерархии*в разделе **пользовательского интерфейса**и добавьте **панели**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="81b0b-284">Это **панели** предоставит фон, текст, который будет отображаться в сцене.</span><span class="sxs-lookup"><span data-stu-id="81b0b-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="81b0b-285">Щелкните правой кнопкой мыши **панели** в *панели иерархии*в разделе **пользовательского интерфейса**и добавьте **текстовый объект**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="81b0b-286">Повторите этот процесс, пока не будут созданы четыре объекта текст пользовательского интерфейса в целом (подсказка: при наличии первый объект «Text» выбран, можно просто нажать клавишу **«Ctrl» + было "**, его придется продублировать, пока у вас будет четыре в целом).</span><span class="sxs-lookup"><span data-stu-id="81b0b-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="81b0b-287">Для каждого **текстовый объект**, выберите его и использовать ниже таблицы для установки параметров *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="81b0b-288">Для *преобразования Rect* компонента:</span><span class="sxs-lookup"><span data-stu-id="81b0b-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="81b0b-289">Имя</span><span class="sxs-lookup"><span data-stu-id="81b0b-289">Name</span></span>                   | <span data-ttu-id="81b0b-290">Преобразование - *позиции*</span><span class="sxs-lookup"><span data-stu-id="81b0b-290">Transform - *Position*</span></span>             | <span data-ttu-id="81b0b-291">Ширина</span><span class="sxs-lookup"><span data-stu-id="81b0b-291">Width</span></span>      | <span data-ttu-id="81b0b-292">Высота</span><span class="sxs-lookup"><span data-stu-id="81b0b-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="81b0b-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="81b0b-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="81b0b-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="81b0b-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="81b0b-295">300</span><span class="sxs-lookup"><span data-stu-id="81b0b-295">300</span></span>        | <span data-ttu-id="81b0b-296">30</span><span class="sxs-lookup"><span data-stu-id="81b0b-296">30</span></span>        |
        | <span data-ttu-id="81b0b-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="81b0b-297">AzureResponseLabel</span></span>     | <span data-ttu-id="81b0b-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="81b0b-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="81b0b-299">300</span><span class="sxs-lookup"><span data-stu-id="81b0b-299">300</span></span>        | <span data-ttu-id="81b0b-300">30</span><span class="sxs-lookup"><span data-stu-id="81b0b-300">30</span></span>        |
        | <span data-ttu-id="81b0b-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="81b0b-301">DictationLabel</span></span>         | <span data-ttu-id="81b0b-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="81b0b-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="81b0b-303">300</span><span class="sxs-lookup"><span data-stu-id="81b0b-303">300</span></span>        | <span data-ttu-id="81b0b-304">30</span><span class="sxs-lookup"><span data-stu-id="81b0b-304">30</span></span>        |
        | <span data-ttu-id="81b0b-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="81b0b-305">TranslationResultLabel</span></span> | <span data-ttu-id="81b0b-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="81b0b-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="81b0b-307">300</span><span class="sxs-lookup"><span data-stu-id="81b0b-307">300</span></span>        | <span data-ttu-id="81b0b-308">30</span><span class="sxs-lookup"><span data-stu-id="81b0b-308">30</span></span>        |


    2. <span data-ttu-id="81b0b-309">Для **текст (скрипт)** компонента:</span><span class="sxs-lookup"><span data-stu-id="81b0b-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="81b0b-310">Имя</span><span class="sxs-lookup"><span data-stu-id="81b0b-310">Name</span></span>                   | <span data-ttu-id="81b0b-311">Текста</span><span class="sxs-lookup"><span data-stu-id="81b0b-311">Text</span></span>               | <span data-ttu-id="81b0b-312">Размер шрифта</span><span class="sxs-lookup"><span data-stu-id="81b0b-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="81b0b-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="81b0b-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="81b0b-314">Состояние "микрофон":</span><span class="sxs-lookup"><span data-stu-id="81b0b-314">Microphone Status:</span></span> | <span data-ttu-id="81b0b-315">20</span><span class="sxs-lookup"><span data-stu-id="81b0b-315">20</span></span>           |
        | <span data-ttu-id="81b0b-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="81b0b-316">AzureResponseLabel</span></span>     | <span data-ttu-id="81b0b-317">Azure веб-ответа</span><span class="sxs-lookup"><span data-stu-id="81b0b-317">Azure Web Response</span></span> | <span data-ttu-id="81b0b-318">20</span><span class="sxs-lookup"><span data-stu-id="81b0b-318">20</span></span>           |
        | <span data-ttu-id="81b0b-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="81b0b-319">DictationLabel</span></span>         |   <span data-ttu-id="81b0b-320">Вы только что сказали:</span><span class="sxs-lookup"><span data-stu-id="81b0b-320">You just said:</span></span>   | <span data-ttu-id="81b0b-321">20</span><span class="sxs-lookup"><span data-stu-id="81b0b-321">20</span></span>           |
        | <span data-ttu-id="81b0b-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="81b0b-322">TranslationResultLabel</span></span> |    <span data-ttu-id="81b0b-323">Перевод:</span><span class="sxs-lookup"><span data-stu-id="81b0b-323">Translation:</span></span>    | <span data-ttu-id="81b0b-324">20</span><span class="sxs-lookup"><span data-stu-id="81b0b-324">20</span></span>           |

        ![Введите соответствующие значения для меток пользовательского интерфейса.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="81b0b-326">Кроме того, сделать стиль шрифта **Полужирный**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="81b0b-327">Это сделает текст более удобным для чтения.</span><span class="sxs-lookup"><span data-stu-id="81b0b-327">This will make the text easier to read.</span></span>

        ![Жирный шрифт.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="81b0b-329">Для каждого *текст пользовательского интерфейса объекта* в [Глава 5](#chapter-5--create-the-results-class), создайте новый *дочерних* **текст пользовательского интерфейса объекта**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="81b0b-330">Эти дочерние объекты будут отображаться выходные данные приложения.</span><span class="sxs-lookup"><span data-stu-id="81b0b-330">These children will display the output of the application.</span></span> <span data-ttu-id="81b0b-331">Создание *дочерних* объектов через щелкните правой кнопкой мыши ваш предполагаемого родительского (например *MicrophoneStatusLabel*), а затем выберите **пользовательского интерфейса** , а затем выберите **текст**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="81b0b-332">Для каждого из этих дочерних элементов, выберите его и используйте ниже таблицы для установки параметров на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="81b0b-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="81b0b-333">Для **преобразования Rect** компонента:</span><span class="sxs-lookup"><span data-stu-id="81b0b-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="81b0b-334">Имя</span><span class="sxs-lookup"><span data-stu-id="81b0b-334">Name</span></span>                  | <span data-ttu-id="81b0b-335">Преобразование - *позиции*</span><span class="sxs-lookup"><span data-stu-id="81b0b-335">Transform - *Position*</span></span> | <span data-ttu-id="81b0b-336">Ширина</span><span class="sxs-lookup"><span data-stu-id="81b0b-336">Width</span></span>      | <span data-ttu-id="81b0b-337">Высота</span><span class="sxs-lookup"><span data-stu-id="81b0b-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="81b0b-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="81b0b-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="81b0b-339">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="81b0b-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="81b0b-340">300</span><span class="sxs-lookup"><span data-stu-id="81b0b-340">300</span></span>        | <span data-ttu-id="81b0b-341">30</span><span class="sxs-lookup"><span data-stu-id="81b0b-341">30</span></span>        |
        | <span data-ttu-id="81b0b-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="81b0b-342">AzureResponseText</span></span>     | <span data-ttu-id="81b0b-343">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="81b0b-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="81b0b-344">300</span><span class="sxs-lookup"><span data-stu-id="81b0b-344">300</span></span>        | <span data-ttu-id="81b0b-345">30</span><span class="sxs-lookup"><span data-stu-id="81b0b-345">30</span></span>        |
        | <span data-ttu-id="81b0b-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="81b0b-346">DictationText</span></span>         | <span data-ttu-id="81b0b-347">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="81b0b-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="81b0b-348">300</span><span class="sxs-lookup"><span data-stu-id="81b0b-348">300</span></span>        | <span data-ttu-id="81b0b-349">30</span><span class="sxs-lookup"><span data-stu-id="81b0b-349">30</span></span>        |
        | <span data-ttu-id="81b0b-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="81b0b-350">TranslationResultText</span></span> | <span data-ttu-id="81b0b-351">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="81b0b-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="81b0b-352">300</span><span class="sxs-lookup"><span data-stu-id="81b0b-352">300</span></span>        | <span data-ttu-id="81b0b-353">30</span><span class="sxs-lookup"><span data-stu-id="81b0b-353">30</span></span>        |

    2. <span data-ttu-id="81b0b-354">Для **текст (скрипт)** компонента:</span><span class="sxs-lookup"><span data-stu-id="81b0b-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="81b0b-355">Имя</span><span class="sxs-lookup"><span data-stu-id="81b0b-355">Name</span></span>                  | <span data-ttu-id="81b0b-356">Текста</span><span class="sxs-lookup"><span data-stu-id="81b0b-356">Text</span></span>          | <span data-ttu-id="81b0b-357">Размер шрифта</span><span class="sxs-lookup"><span data-stu-id="81b0b-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="81b0b-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="81b0b-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="81b0b-359">??</span><span class="sxs-lookup"><span data-stu-id="81b0b-359">??</span></span>       | <span data-ttu-id="81b0b-360">20</span><span class="sxs-lookup"><span data-stu-id="81b0b-360">20</span></span>           |
        | <span data-ttu-id="81b0b-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="81b0b-361">AzureResponseText</span></span>     |      <span data-ttu-id="81b0b-362">??</span><span class="sxs-lookup"><span data-stu-id="81b0b-362">??</span></span>       | <span data-ttu-id="81b0b-363">20</span><span class="sxs-lookup"><span data-stu-id="81b0b-363">20</span></span>           |
        | <span data-ttu-id="81b0b-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="81b0b-364">DictationText</span></span>         |      <span data-ttu-id="81b0b-365">??</span><span class="sxs-lookup"><span data-stu-id="81b0b-365">??</span></span>       | <span data-ttu-id="81b0b-366">20</span><span class="sxs-lookup"><span data-stu-id="81b0b-366">20</span></span>           |
        | <span data-ttu-id="81b0b-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="81b0b-367">TranslationResultText</span></span> |      <span data-ttu-id="81b0b-368">??</span><span class="sxs-lookup"><span data-stu-id="81b0b-368">??</span></span>       | <span data-ttu-id="81b0b-369">20</span><span class="sxs-lookup"><span data-stu-id="81b0b-369">20</span></span>           |

9. <span data-ttu-id="81b0b-370">Затем выберите параметр выравнивания «центр» для каждого компонента текста:</span><span class="sxs-lookup"><span data-stu-id="81b0b-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![Выравнивание текста.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="81b0b-372">Чтобы обеспечить **дочерних текст пользовательского интерфейса** объектов можно легко читать, изменять их *цвет*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="81b0b-373">Это можно сделать, нажав кнопку на панели (в настоящее время «черный») рядом с полем *цвет*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Введите соответствующие значения для выходных данных текст пользовательского интерфейса.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="81b0b-375">Затем в новый, слишком мало, *цвет* измените *цвет Hex* для: **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="81b0b-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Обновите цвет на синий.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="81b0b-377">Ниже приведен способ **пользовательского интерфейса** должен выглядеть.</span><span class="sxs-lookup"><span data-stu-id="81b0b-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="81b0b-378">В *панели иерархии*:</span><span class="sxs-lookup"><span data-stu-id="81b0b-378">In the *Hierarchy Panel*:</span></span>

        ![Иметь иерархию в предоставленный структуры.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="81b0b-380">В *сцены* и *игр представления*:</span><span class="sxs-lookup"><span data-stu-id="81b0b-380">In the *Scene* and *Game Views*:</span></span>

        ![У представлений сцены и игра в ту же структуру.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="81b0b-382">Глава 5 – создать класс результатов</span><span class="sxs-lookup"><span data-stu-id="81b0b-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="81b0b-383">Первый скрипт, чтобы создать *результаты* класс, который отвечает за предоставление способ увидеть результаты преобразования.</span><span class="sxs-lookup"><span data-stu-id="81b0b-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="81b0b-384">Класс хранит и отображаются следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="81b0b-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="81b0b-385">Результат ответа из Azure.</span><span class="sxs-lookup"><span data-stu-id="81b0b-385">The response result from Azure.</span></span>
- <span data-ttu-id="81b0b-386">Состояние "микрофон".</span><span class="sxs-lookup"><span data-stu-id="81b0b-386">The microphone status.</span></span> 
- <span data-ttu-id="81b0b-387">Результат диктовки (голоса в текст).</span><span class="sxs-lookup"><span data-stu-id="81b0b-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="81b0b-388">Результат преобразования.</span><span class="sxs-lookup"><span data-stu-id="81b0b-388">The result of the translation.</span></span>

<span data-ttu-id="81b0b-389">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="81b0b-389">To create this class:</span></span> 

1.  <span data-ttu-id="81b0b-390">Щелкните правой кнопкой мыши в *проекта панели*, затем **Создать > Папка**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="81b0b-391">Назовите папку **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-391">Name the folder **Scripts**.</span></span> 
 
    ![Создайте папку scripts.](images/AzureLabs-Lab1-31.png)

    ![Откройте папку «скрипты».](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="81b0b-394">С помощью **сценариев** папке создайте, дважды щелкните его, чтобы открыть.</span><span class="sxs-lookup"><span data-stu-id="81b0b-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="81b0b-395">Затем в этой папке, щелкните правой кнопкой мыши и выберите **Создать >** затем  **C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="81b0b-396">Назовите сценарий *результаты*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-396">Name the script *Results*.</span></span> 

    ![Создание первого скрипта.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="81b0b-398">Дважды щелкните новый *результатов* скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="81b0b-399">Вставьте следующие пространства имен:</span><span class="sxs-lookup"><span data-stu-id="81b0b-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="81b0b-400">Внутри класса вставьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="81b0b-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="81b0b-401">Затем добавьте *Awake()* метод, который будет вызываться при инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="81b0b-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="81b0b-402">Наконец добавьте методы, которые отвечают за вывод различные сведения результатов в пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="81b0b-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="81b0b-403">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="81b0b-404">Глава 6 – создать *MicrophoneManager* класса</span><span class="sxs-lookup"><span data-stu-id="81b0b-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="81b0b-405">Вы собираетесь создать второй класс — *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="81b0b-406">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="81b0b-406">This class is responsible for:</span></span>

- <span data-ttu-id="81b0b-407">Обнаружение устройства записи, подключенные к гарнитуры или machine (выбирается по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="81b0b-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="81b0b-408">Запись звука (голос) и использовать режим диктовки сохранит их в виде строки.</span><span class="sxs-lookup"><span data-stu-id="81b0b-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="81b0b-409">После приостановлена голоса, отправки диктовки к классу Translator.</span><span class="sxs-lookup"><span data-stu-id="81b0b-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="81b0b-410">Разместите метод, который можно остановить записи голоса, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="81b0b-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="81b0b-411">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="81b0b-411">To create this class:</span></span> 
1.  <span data-ttu-id="81b0b-412">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="81b0b-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="81b0b-413">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="81b0b-414">Назовите сценарий *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="81b0b-415">Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81b0b-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="81b0b-416">Обновите пространства имен должны совпадать, как показано ниже, в верхней части *MicrophoneManager* класса:</span><span class="sxs-lookup"><span data-stu-id="81b0b-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="81b0b-417">Затем добавьте следующие переменные внутри *MicrophoneManager* класса:</span><span class="sxs-lookup"><span data-stu-id="81b0b-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="81b0b-418">Код для *Awake()* и *Start()* методы теперь должен быть добавлен.</span><span class="sxs-lookup"><span data-stu-id="81b0b-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="81b0b-419">Это будет вызываться при инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="81b0b-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="81b0b-420">Вы можете *удалить* *Update()* метод, так как этот класс не будет его использовать.</span><span class="sxs-lookup"><span data-stu-id="81b0b-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="81b0b-421">Теперь необходимо методы, которые приложение использует для запуска и остановки записи голоса и передать его в *Translator* класса, который вы создадите в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="81b0b-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="81b0b-422">Скопируйте следующий код и вставьте его под *Start()* метод.</span><span class="sxs-lookup"><span data-stu-id="81b0b-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="81b0b-423">Хотя это приложение не будет выполнять его, использовать *StopCapturingAudio()* метод также предоставляется здесь, вам понадобится реализовать возможность остановки записи звука в приложении.</span><span class="sxs-lookup"><span data-stu-id="81b0b-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="81b0b-424">Теперь необходимо добавить обработчик, диктовки, который будет вызываться при остановке голоса.</span><span class="sxs-lookup"><span data-stu-id="81b0b-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="81b0b-425">Этот метод затем передаст надиктованного текста для *Translator* класса.</span><span class="sxs-lookup"><span data-stu-id="81b0b-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="81b0b-426">Не забудьте сохранить изменения в Visual Studio перед возвратом к Unity.</span><span class="sxs-lookup"><span data-stu-id="81b0b-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="81b0b-427">На этом этапе вы заметите ошибку в *консоли редактора Unity* панели («имя «Translator» не существует...»).</span><span class="sxs-lookup"><span data-stu-id="81b0b-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="81b0b-428">Это так, как код ссылается на *Translator* класс, который будет создан в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="81b0b-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="81b0b-429">Глава 7 – вызов к службе Azure и переводчика</span><span class="sxs-lookup"><span data-stu-id="81b0b-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="81b0b-430">— Последний скрипт, чтобы создать *Translator* класса.</span><span class="sxs-lookup"><span data-stu-id="81b0b-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="81b0b-431">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="81b0b-431">This class is responsible for:</span></span>

-   <span data-ttu-id="81b0b-432">Проверка подлинности приложения с помощью *Azure*, в exchange для **маркер проверки подлинности**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="81b0b-433">Используйте **маркер проверки подлинности** для отправки текста (полученные от *MicrophoneManager* класс) для перевода.</span><span class="sxs-lookup"><span data-stu-id="81b0b-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="81b0b-434">Получать переведенные результат и передать его в *результаты* класс для отображения в пользовательском Интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="81b0b-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="81b0b-435">Для создания данного класса:</span><span class="sxs-lookup"><span data-stu-id="81b0b-435">To create this Class:</span></span> 
1.  <span data-ttu-id="81b0b-436">Перейдите к **сценариев** папку, созданную ранее.</span><span class="sxs-lookup"><span data-stu-id="81b0b-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="81b0b-437">Щелкните правой кнопкой мыши в **проекта панели**, **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="81b0b-438">Вызовите сценарий *Translator*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="81b0b-439">Дважды щелкните новый *Translator* скрипт, чтобы открыть его **с помощью Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="81b0b-440">Добавьте следующие пространства имен в начало файла:</span><span class="sxs-lookup"><span data-stu-id="81b0b-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="81b0b-441">Затем добавьте следующие переменные внутри *Translator* класса:</span><span class="sxs-lookup"><span data-stu-id="81b0b-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="81b0b-442">Языки, которые вставлены в языках **перечисления** только в качестве примера.</span><span class="sxs-lookup"><span data-stu-id="81b0b-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="81b0b-443">Вы можете добавить более, при необходимости; [API поддерживает более чем 60 языков](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (включая обычного русского или Марсианского)!</span><span class="sxs-lookup"><span data-stu-id="81b0b-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="81b0b-444">Существует [более интерактивной страница, которая содержит доступные языки](https://www.microsoft.com/translator/business/languages/), но имейте в виду, страница отображается только для работы, если язык сайта имеет значение "en-us' (и на сайте Microsoft будет скорее всего, перенаправление на Ваш родной язык).</span><span class="sxs-lookup"><span data-stu-id="81b0b-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="81b0b-445">Вы можете изменить язык сайта в нижней части страницы или изменение URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="81b0b-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="81b0b-446">**AuthorizationKey** значение в приведенном выше фрагменте кода должно быть **ключ** полученный при подписке на *API перевода текстов Azure*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="81b0b-447">Это изложено в [главе 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="81b0b-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="81b0b-448">Код для *Awake()* и *Start()* методы теперь должен быть добавлен.</span><span class="sxs-lookup"><span data-stu-id="81b0b-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="81b0b-449">В этом случае код будет сделать вызов к *Azure* с помощью авторизации ключа, чтобы получить *маркера*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="81b0b-450">Токен истекает через 10 минут.</span><span class="sxs-lookup"><span data-stu-id="81b0b-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="81b0b-451">В зависимости от сценария для приложения может потребоваться внести же сопрограммы вызывать несколько раз.</span><span class="sxs-lookup"><span data-stu-id="81b0b-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="81b0b-452">Сопрограммы для получения маркера выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="81b0b-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="81b0b-453">Если вы изменяете имя метода IEnumerator **GetTokenCoroutine()**, необходимо обновить *StartCoroutine* и *StopCoroutine* вызовите строковые значения в приведенном выше коде.</span><span class="sxs-lookup"><span data-stu-id="81b0b-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="81b0b-454">[Согласно документации по Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), чтобы остановить определенный *Соподпрограмме*, необходимо использовать метод значения строк.</span><span class="sxs-lookup"><span data-stu-id="81b0b-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="81b0b-455">Затем добавьте соподпрограмме (с «поддержка» методом stream прямо под ним) для получения перевода текста, полученных *MicrophoneManager* класса.</span><span class="sxs-lookup"><span data-stu-id="81b0b-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="81b0b-456">Этот код создает строку запроса для отправки *API перевода текстов Azure*, а затем использует внутренний класс Unity UnityWebRequest звонки в конечную точку с помощью строки запроса «Get».</span><span class="sxs-lookup"><span data-stu-id="81b0b-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="81b0b-457">Результат затем используется для задания преобразования в объекте результатов.</span><span class="sxs-lookup"><span data-stu-id="81b0b-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="81b0b-458">В приведенном ниже коде показана реализация:</span><span class="sxs-lookup"><span data-stu-id="81b0b-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="81b0b-459">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="81b0b-460">Глава 8 – Настройка сцене Unity</span><span class="sxs-lookup"><span data-stu-id="81b0b-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="81b0b-461">Обратно в редакторе Unity, щелкните и перетащите *результатов* класс *из* **сценарии** папку **Main Camera** объекта в  *Панель иерархии*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="81b0b-462">Щелкните **Main Camera** и просмотрите *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="81b0b-463">Можно будет заметить, что в только что добавленного *скрипт* компонента есть четыре поля с пустыми значениями.</span><span class="sxs-lookup"><span data-stu-id="81b0b-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="81b0b-464">Это выходные данные ссылки на свойства в коде.</span><span class="sxs-lookup"><span data-stu-id="81b0b-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="81b0b-465">Перетащите соответствующий **текст** объектов из *панели иерархии* для этих четырех позициях, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="81b0b-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Обновите ссылки на целевую с заданными значениями.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="81b0b-467">Далее щелкните и перетащите *Translator* класса из **сценарии** папку **Main Camera** объекта в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="81b0b-468">Затем щелкните и перетащите *MicrophoneManager* класса из **сценарии** папку **Main Camera** объекта в *панели иерархии*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="81b0b-469">Наконец, щелкните **Main Camera** и просмотрите *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="81b0b-470">Обратите внимание, что в скрипте, который вы перетащили на, есть два раскрывающихся списках, на которые вы сможете задать языки.</span><span class="sxs-lookup"><span data-stu-id="81b0b-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Убедитесь, что языки предполагаемого перевода являются входными данными.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="81b0b-472">Глава 9-теста в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="81b0b-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="81b0b-473">На этом этапе необходимо проверить, что сцены реализован правильно.</span><span class="sxs-lookup"><span data-stu-id="81b0b-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="81b0b-474">Убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="81b0b-474">Ensure that:</span></span>

- <span data-ttu-id="81b0b-475">Все параметры, упомянутые в [главе 1](#chapter-1--the-azure-portal) заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="81b0b-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="81b0b-476">*Результатов*, *Translator*, и *MicrophoneManager*, скрипты, присоединяются к **Main Camera** объекта.</span><span class="sxs-lookup"><span data-stu-id="81b0b-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="81b0b-477">Размещен ваш *API перевода текстов Azure* службы **ключ** в **authorizationKey** переменную *Translator* Скрипт.</span><span class="sxs-lookup"><span data-stu-id="81b0b-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="81b0b-478">Все поля в *главной панели Инспектора камеры* назначаются должным образом.</span><span class="sxs-lookup"><span data-stu-id="81b0b-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="81b0b-479">Микрофон работает при выполнении в сцену (если это не так, убедитесь, что микрофон присоединенного *по умолчанию* устройства и что у вас есть [его правильно установить в Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span><span class="sxs-lookup"><span data-stu-id="81b0b-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="81b0b-480">Можно проверить иммерсивных гарнитура, нажав клавишу **воспроизведение** кнопку *редактора Unity*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="81b0b-481">Приложение должно работает через присоединенное иммерсивных гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="81b0b-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="81b0b-482">Если появится сообщение об ошибке, в консоли Unity о аудиоустройства по умолчанию изменение, сцены может не работать должным образом.</span><span class="sxs-lookup"><span data-stu-id="81b0b-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="81b0b-483">Это из-за способа на портале смешанной реальности имеет дело с встроенные микрофоны применяется, в которых они имеются.</span><span class="sxs-lookup"><span data-stu-id="81b0b-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="81b0b-484">Если эта ошибка возникает, просто остановить сцены и запустить снова и вещи должны работать как ожидалось.</span><span class="sxs-lookup"><span data-stu-id="81b0b-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="81b0b-485">Глава 10 – построение решения для универсальной платформы Windows и загрузки неопубликованных приложений на локальном компьютере</span><span class="sxs-lookup"><span data-stu-id="81b0b-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="81b0b-486">Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.</span><span class="sxs-lookup"><span data-stu-id="81b0b-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="81b0b-487">Перейдите к **параметры сборки**: **Файл > Параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="81b0b-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="81b0b-488">Из **параметры построения** окно, нажмите кнопку **построения**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Создавайте сцене Unity.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="81b0b-490">Если не сделали, установите **Unity C# проекты**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="81b0b-491">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-491">Click **Build**.</span></span> <span data-ttu-id="81b0b-492">Unity приведет к запуску *проводнике* окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в.</span><span class="sxs-lookup"><span data-stu-id="81b0b-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="81b0b-493">Создайте эту папку и назовите его *приложения*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="81b0b-494">Затем с помощью *приложения* папку, нажмите клавишу **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="81b0b-495">Unity начнется построение проекта для *приложения* папки.</span><span class="sxs-lookup"><span data-stu-id="81b0b-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="81b0b-496">Один раз Unity завершил построение (может занять некоторое время), он будет открыт *проводнике* окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).</span><span class="sxs-lookup"><span data-stu-id="81b0b-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="81b0b-497">Глава 11 — развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="81b0b-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="81b0b-498">Для развертывания приложения:</span><span class="sxs-lookup"><span data-stu-id="81b0b-498">To deploy your application:</span></span>

1.  <span data-ttu-id="81b0b-499">Перейдите к новой сборки Unity ( *приложения* папки) и откройте файл решения с *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="81b0b-500">В списке выберите конфигурацию решения **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="81b0b-501">В платформу решения, выберите **x86**, **локальный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="81b0b-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="81b0b-502">Для Microsoft HoloLens, может быть проще устанавливать равным *удаленный компьютер*, таким образом, не связанном устройстве на компьютер.</span><span class="sxs-lookup"><span data-stu-id="81b0b-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="81b0b-503">Однако необходимо будет выполнить следующее:</span><span class="sxs-lookup"><span data-stu-id="81b0b-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="81b0b-504">Знать **IP-адрес** из HoloLens, которую можно найти в *параметры > сеть и Интернет > Wi-Fi > Дополнительно*; IPv4 — это адрес, следует использовать.</span><span class="sxs-lookup"><span data-stu-id="81b0b-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="81b0b-505">Убедитесь, *режим разработчика* — **на**; найдено в *параметры > обновление и безопасность > для разработчиков*.</span><span class="sxs-lookup"><span data-stu-id="81b0b-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="81b0b-507">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение** для загрузки неопубликованных приложений на вашем ПК.</span><span class="sxs-lookup"><span data-stu-id="81b0b-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="81b0b-508">Приложения появятся в списке установленных приложений, Готово к запуску.</span><span class="sxs-lookup"><span data-stu-id="81b0b-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="81b0b-509">После запуска приложение попросит авторизовать доступ к микрофону.</span><span class="sxs-lookup"><span data-stu-id="81b0b-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="81b0b-510">Убедитесь, что щелкните **Да** кнопки.</span><span class="sxs-lookup"><span data-stu-id="81b0b-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="81b0b-511">Теперь вы готовы начать перевод!</span><span class="sxs-lookup"><span data-stu-id="81b0b-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="81b0b-512">Готового приложения API перевода текстов</span><span class="sxs-lookup"><span data-stu-id="81b0b-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="81b0b-513">Поздравляем, вы создали приложение смешанной реальности, которое использует API Azure перевода текста для преобразования речи в переведенный текст.</span><span class="sxs-lookup"><span data-stu-id="81b0b-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Конечный продукт.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="81b0b-515">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="81b0b-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="81b0b-516">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="81b0b-516">Exercise 1</span></span>

<span data-ttu-id="81b0b-517">Можно добавить функциональные возможности преобразования текста в речь в приложение таким образом, чтобы возвращаемый текст произнесении?</span><span class="sxs-lookup"><span data-stu-id="81b0b-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="81b0b-518">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="81b0b-518">Exercise 2</span></span>

<span data-ttu-id="81b0b-519">Позволяют пользователю изменять источник и выходные данные языки («from» и «по») в само приложение, приложение необходимо перестроить, каждый раз, чтобы изменить языки.</span><span class="sxs-lookup"><span data-stu-id="81b0b-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
