---
title: Г-н и 312 Azure — интеграция программ-роботов
description: Завершите этот курс, чтобы узнать, как создать и развернуть программы-робота, используя Microsoft Bot Framework версии 4 и взаимодействовать с ним в приложении смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, unity, учебник, api, компьютерного зрения, hololens, создающий эффект присутствия, vr, microsoft bot framework v4, программ-роботов приложение web, bot framework, программ-роботов microsoft
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604983"
---
>[!NOTE]
><span data-ttu-id="0ee0f-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0ee0f-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0ee0f-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0ee0f-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0ee0f-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0ee0f-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="0ee0f-110">Г-н и Azure 312: Интеграция программ-роботов</span><span class="sxs-lookup"><span data-stu-id="0ee0f-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="0ee0f-111">В рамках этого курса вы узнаете, как создать и развернуть программы-робота, используя Microsoft Bot Framework версии 4 и взаимодействовать с ним через приложение Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="0ee0f-112">**Microsoft Bot Framework V4** — это набор API-интерфейсов, предназначенных предоставляет разработчикам средства для создания масштабируемые программ-роботов приложение.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="0ee0f-113">Дополнительные сведения см. в статье [страницы Microsoft Bot Framework](https://dev.botframework.com/) или [V4 репозитория](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="0ee0f-114">После прохождения этого курса вы сможете создать это приложение Windows Mixed Reality, которое будет осуществлять следующее:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="0ee0f-115">Используйте **коснитесь жест** для запуска программ-роботов, прослушивание голоса пользователей.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="0ee0f-116">Если пользователь говорилось что-то, бот будет пытаться предоставить ответ.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="0ee0f-117">Отобразить ответ программы-роботы как текст, расположенный рядом с программ-роботов, в сцене Unity.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="0ee0f-118">В приложении зависит от пользователя о том, как интегрировать результаты проектированию.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="0ee0f-119">Этот курс призван научить позволяют интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="0ee0f-120">Это задание может использовать знание, что вы получите из этого курса можно улучшить приложение смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="0ee0f-121">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="0ee0f-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0ee0f-122">Курс</span><span class="sxs-lookup"><span data-stu-id="0ee0f-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0ee0f-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0ee0f-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0ee0f-124"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="0ee0f-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0ee0f-125">Г-н и Azure 312: Интеграция программ-роботов</span><span class="sxs-lookup"><span data-stu-id="0ee0f-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="0ee0f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="0ee0f-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0ee0f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="0ee0f-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="0ee0f-128">Хотя этот курс основное внимание уделяется HoloLens, можно также применить полученные знания в этот курс поможет вам Windows Mixed Reality иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="0ee0f-129">Поскольку иммерсивную (VR) не имеют доступных камеры, вам потребуется внешний камеры, подключенном к ПК.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="0ee0f-130">При выполнении, а также курс, вы увидите заметки обо всех изменениях, может потребоваться использовать для поддержки иммерсивную (VR).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0ee0f-131">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="0ee0f-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0ee0f-132">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с помощью Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0ee0f-133">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="0ee0f-134">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="0ee0f-135">Рекомендуется следующее оборудование и программное обеспечение для этого курса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0ee0f-136">На Компьютере, разработки [совместимы с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для иммерсивных разработки Гарнитура (VR)</span><span class="sxs-lookup"><span data-stu-id="0ee0f-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="0ee0f-137">Windows 10 Fall Creators Update (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="0ee0f-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0ee0f-138">Последний пакет SDK Windows 10</span><span class="sxs-lookup"><span data-stu-id="0ee0f-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0ee0f-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="0ee0f-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0ee0f-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0ee0f-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="0ee0f-141">Объект [иммерсивных (VR) гарнитуры смешанной реальности Windows](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="0ee0f-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="0ee0f-142">Доступ к Интернету для Azure, а также для извлечения программ-роботов Azure.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="0ee0f-143">Дополнительные сведения [щелкните эту ссылку](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="0ee0f-144">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="0ee0f-144">Before you start</span></span>

1.  <span data-ttu-id="0ee0f-145">Чтобы избежать возникновения проблем сборки этого проекта, настоятельно рекомендуется создать проект, упомянутые в этом руководстве в корень или рядом с корневой папки (пути к папкам long может привести к проблемам во время сборки).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="0ee0f-146">Настроить и проверить ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="0ee0f-147">Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="0ee0f-148">Рекомендуется для выполнения калибровки и настройке датчика, когда начинается при разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="0ee0f-149">Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="0ee0f-150">Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="0ee0f-151">Глава 1 – Создание приложения программ-роботов</span><span class="sxs-lookup"><span data-stu-id="0ee0f-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="0ee0f-152">Первым шагом является создание бота как локальное приложение ASP.Net Core Web.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="0ee0f-153">После завершения и протестировали его, как опубликовать его на портал Azure.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="0ee0f-154">Откройте Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-154">Open Visual Studio.</span></span> <span data-ttu-id="0ee0f-155">Создайте новый проект, выберите **веб-приложение ASP NET Core** в качестве типа проекта (его будет найти в подразделе .NET Core) и назовите его **MyBot**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="0ee0f-156">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-156">Click **OK**.</span></span>

2.  <span data-ttu-id="0ee0f-157">В окне, которое будет отображаться выберите **пустой**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="0ee0f-158">Также убедитесь, что целевой объект имеет значение **ASP NET Core 2.0** и проверки подлинности значение **без проверки подлинности**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="0ee0f-159">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-159">Click **OK**.</span></span>  

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="0ee0f-161">Теперь будет открыто решение.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-161">The solution will now open.</span></span> <span data-ttu-id="0ee0f-162">Щелкните правой кнопкой мыши на решении **Mybot** в **обозревателе решений** и щелкнуть **управление пакетами NuGet для решения**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="0ee0f-164">В **Обзор** вкладке, поиск **Microsoft.Bot.Builder.Integration.AspNet.Core** (Убедитесь, что у вас есть **включения предварительного выпуска** флажок установлен).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="0ee0f-165">Выберите версию пакета **4.0.1-preview**и установите флажки проекта.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="0ee0f-166">Нажмите кнопку на **установить**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-166">Then click on **Install**.</span></span> <span data-ttu-id="0ee0f-167">Теперь вы установили библиотеки, необходимые для **Bot Framework версии 4**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="0ee0f-168">Закройте страницу NuGet.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-168">Close the NuGet page.</span></span>

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="0ee0f-170">Щелкните правой кнопкой мыши ваш *проекта*, **MyBot**в **обозревателе решений** и щелкнуть **добавить** **|** **Класс**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="0ee0f-172">Назовите класс **MyBot** и щелкнуть **добавить**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="0ee0f-174">Повторите предыдущие точек, чтобы создать другой класс с именем **ConversationContext**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="0ee0f-175">Щелкните правой кнопкой мыши **wwwroot** в **обозревателе решений** и щелкнуть **добавить** **|** **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="0ee0f-176">Выберите **HTML-страницу** (вы найдете ее в разделе Web подраздела).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="0ee0f-177">Назовите файл **default.html**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-177">Name the file **default.html**.</span></span> <span data-ttu-id="0ee0f-178">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-178">Click **Add**.</span></span>

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="0ee0f-180">Список классов и объектов в **обозревателе решений** должен выглядеть как на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Создание приложения программ-роботов](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="0ee0f-182">Дважды щелкните **ConversationContext** класса.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="0ee0f-183">Этот класс отвечает за хранение переменные, используемые задачей бота для поддержания контекста диалога.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="0ee0f-184">Эти значения контекста диалога сохраняются в экземпляре этого класса, так как любой экземпляр **MyBot** класс будет обновляться каждый раз при получении действия.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="0ee0f-185">Добавьте следующий код к классу:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="0ee0f-186">Дважды щелкните **MyBot** класса.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="0ee0f-187">Этот класс будет размещаться обработчиков, вызываемых любого входящего действия от клиента.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="0ee0f-188">В этом классе вы добавите код, используемый для создания диалога между бота-помощника и клиента.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="0ee0f-189">Как упоминалось ранее, экземпляр этого класса инициализируется каждый раз при получении действия.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="0ee0f-190">Добавьте следующий код для этого класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="0ee0f-191">Дважды щелкните **запуска** класса.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="0ee0f-192">Этот класс будет инициализировать бота.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-192">This class will initialize the bot.</span></span> <span data-ttu-id="0ee0f-193">Добавьте следующий код к классу:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="0ee0f-194">Откройте **программы** файле класса и проверьте код, в нем зависит от того, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="0ee0f-195">Не забудьте сохранить изменения, чтобы сделать это, перейдите к **файл** > **сохранить все**, на панели инструментов в верхней части Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="0ee0f-196">Глава 2 - Создание службы Azure Bot</span><span class="sxs-lookup"><span data-stu-id="0ee0f-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="0ee0f-197">Теперь, когда вы создавали код для вашего бота, вам нужно опубликовать его в экземпляр *программ-роботов приложение Web* службы на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="0ee0f-198">В этой главе показано, как создать и настроить службу программ-роботов на Azure и затем их публикация кода.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="0ee0f-199">Во-первых, войдите на портал Azure (https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="0ee0f-200">Если у вас еще нет учетной записи Azure, необходимо будет создать его.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0ee0f-201">Если вы следуете этим руководством, аудитории или лаборатории ситуации, попросите преподавателем или из прокторов для сведения о настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="0ee0f-202">После входа в систему щелкните **создать ресурс** в левом верхнем углу, а поиск *бот веб-приложения*и нажмите кнопку **ввод**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="0ee0f-204">Новая страница будет предоставить описание *программ-роботов приложение Web* службы.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="0ee0f-205">В нижней левой части этой страницы выберите **создать** кнопку, чтобы создать ассоциацию с данным службы.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="0ee0f-207">Когда вы перейдете на **создать**:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="0ee0f-208">Вставить нужный **имя** для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="0ee0f-209">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="0ee0f-210">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0ee0f-211">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0ee0f-212">Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="0ee0f-213">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, [щелкните эту ссылку](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="0ee0f-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="0ee0f-214">Определите расположение для группы ресурсов (Если вы создаете новую группу ресурсов).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="0ee0f-215">Расположение оптимально подойдет в регионе, в котором приложение будет работать.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="0ee0f-216">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="0ee0f-217">Выберите **Ценовая** подходит для вас, если это первое времени на создание *программ-роботов приложение Web* службы, уровень "бесплатный" (с именем F0) должны быть доступны для вас</span><span class="sxs-lookup"><span data-stu-id="0ee0f-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="0ee0f-218">**Имя приложения** можно просто оставить так же, как *имя бота*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="0ee0f-219">Оставьте *шаблона программ-роботов* как **основные (C#)**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="0ee0f-220">*План службы приложений или расположение* должно было автоматически заполняться сведениями для вашей учетной записи.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="0ee0f-221">Задайте **хранилища Azure** , которые нужно использовать для размещения вашего бота.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="0ee0f-222">Если вы не сделали, можно создать его здесь.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="0ee0f-223">Также необходимо будет подтвердить, что мы рассмотрели, положения и условия, применяемые к этой службе.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="0ee0f-224">Нажмите кнопку Создать.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-224">Click Create.</span></span>
 
        ![Создание службы Azure Bot](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="0ee0f-226">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="0ee0f-227">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="0ee0f-229">Щелкните уведомление, чтобы изучить ваш новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="0ee0f-231">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="0ee0f-232">Откроется в новом экземпляре службы Azure.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="0ee0f-234">На этом этапе необходимо настроить функцию, называемую **прямую линию** чтобы разрешить клиентскому приложению взаимодействовать с этой службой программ-роботов.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="0ee0f-235">Щелкните **каналы**, а затем в **добавить основной канал** щелкните **настроить прямую линию канал**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="0ee0f-237">На этой странице вы найдете **секретных ключей** , обеспечивая клиентского приложения для проверки подлинности с помощью программ-роботов.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="0ee0f-238">Щелкните **Показать** кнопку и сделайте копию один из отображаемых ключей, так как он потребуется позже в проекте.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="0ee0f-240">Глава 3 – публикация программ-роботов, программ-роботов приложение в Azure веб-службу</span><span class="sxs-lookup"><span data-stu-id="0ee0f-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="0ee0f-241">Теперь, когда служба будет готов, необходимо опубликовать код программ-роботов, которое вы создали ранее, в только что созданный веб-службу программ-роботов приложение.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="0ee0f-242">Необходимо будет опубликовать бота в службе Azure каждый раз при внесении изменений в решение Bot / code.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="0ee0f-243">Вернитесь к решения Visual Studio, который вы создали ранее.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="0ee0f-244">Щелкните правой кнопкой мыши вашей **MyBot** проекта **обозревателе решений**, затем щелкните **публикации**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Публикация программ-роботов, программ-роботов приложение в Azure веб-службу](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="0ee0f-246">На *выберите целевой объект публикации* щелкните **службы приложений**, затем **выбрать существующее**, наконец, щелкните на **создать профиль** (может потребоваться Щелкните стрелку раскрывающегося списка рядом с *публикации* кнопку, если это не отображается).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Публикация программ-роботов, программ-роботов приложение в Azure веб-службу](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="0ee0f-248">Если вы не еще вошли в учетную запись Майкрософт, что необходимо сделать его здесь.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="0ee0f-249">На **публикации** странице вы найдете это нужно сделать же **подписки** , использованная для *программ-роботов приложение Web* создать службу.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="0ee0f-250">Затем установите **представление** как **группы ресурсов** и в раскрывающемся списке структуру папок, выберите **группы ресурсов** созданный ранее.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="0ee0f-251">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-251">Click **OK**.</span></span> 

    ![Публикация программ-роботов, программ-роботов приложение в Azure веб-службу](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="0ee0f-253">Теперь щелкните **публикации** кнопку и подождите, программ-роботов для публикации (может занять несколько минут).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Публикация программ-роботов, программ-роботов приложение в Azure веб-службу](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="0ee0f-255">Глава 4 – Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="0ee0f-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="0ee0f-256">Следующие запущена типичный набор для разработки с помощью смешанной реальности и, таким образом, — это хороший шаблон для других проектов.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="0ee0f-257">Откройте *Unity* и нажмите кнопку **New**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-257">Open *Unity* and click **New**.</span></span> 

    ![Настройка проекта Unity](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="0ee0f-259">Теперь необходимо будет указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="0ee0f-260">Вставить **Hololens программ-роботов**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="0ee0f-261">Убедитесь, что шаблон проекта присваивается **3D**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="0ee0f-262">Задайте **расположение** в другое место, наиболее подходящего для вас (Помните, что лучше, чем ближе к корневые каталоги).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0ee0f-263">Щелкните **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-263">Then, click **Create project**.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="0ee0f-265">С помощью Unity откройте, стоит проверки по умолчанию **редактор сценариев** присваивается **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0ee0f-266">Перейдите к **изменить > настройки** и затем в окне «Новый» перейдите к **внешние средства**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0ee0f-267">Изменение **внешнего редактора скриптов** для **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="0ee0f-268">Закрыть **предпочтения** окна.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-268">Close the **Preferences** window.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="0ee0f-270">Перейдите к **файл > Параметры сборки** и выберите **универсальной платформы Windows**, затем щелкните **переключить платформу** кнопку, чтобы применить выбранные параметры.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="0ee0f-272">Оставаясь в **файл > Параметры сборки** и убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="0ee0f-273">**Целевое устройство** присваивается **Hololens**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="0ee0f-274">Иммерсивную, задайте **целевое устройство** для *любого устройства*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="0ee0f-275">**Тип сборки** присваивается **D3D**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="0ee0f-276">**Пакет SDK для** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="0ee0f-277">**Версия Visual Studio** присваивается **самую новую установленную**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="0ee0f-278">**Сборка и запуск** присваивается **локального компьютера**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="0ee0f-279">Сохраните сцены и добавить его к сборке.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="0ee0f-280">Это сделать, выбрав **добавьте откройте сцены**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="0ee0f-281">Сохранение окно будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-281">A save window will appear.</span></span>
        
            ![Настройка проекта Unity](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="0ee0f-283">Создайте новую папку и все будущие, сцены, затем выберите **новую папку** кнопку, чтобы создать новую папку, назовите его **сцены**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Настройка проекта Unity](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="0ee0f-285">Откройте только что созданный **сцены** папку, а затем в *имя файла*: текстовое поле, тип **BotScene**, нажмите кнопку на **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="0ee0f-287">Для остальных параметров, в **параметры построения**, следует оставить значение по умолчанию сейчас.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="0ee0f-288">В *параметры построения* щелкните **параметры проигрывателя** кнопки, откроется панель связанных в пространстве где *инспектор* находится.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Настройка проекта Unity](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="0ee0f-290">В этой панели необходимо проверить некоторые настройки:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="0ee0f-291">В **другие параметры** вкладке:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="0ee0f-292">**Версия среды выполнения сценариев** должно быть **экспериментальная (эквивалент 4.6 NET)**; это изменение потребует перезапуска редактора.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="0ee0f-293">**Создание сценариев серверной части** должно быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="0ee0f-294">**Уровень совместимости API** должно быть **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="0ee0f-296">В рамках **параметров публикации** в списке **возможности**, проверьте:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="0ee0f-297">**internetClient**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-297">**InternetClient**</span></span>
        - <span data-ttu-id="0ee0f-298">**"Микрофон"**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-298">**Microphone**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="0ee0f-300">Далее панели в **XR параметры** (под **параметры публикации**), деления **поддерживается виртуальной реальности**, убедитесь, что **смешанной реальности SDK Windows**  добавляется.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="0ee0f-302">Вернитесь в *параметры построения* _Unity C#_  проектов больше не отображается серым, установите флажок рядом с это.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="0ee0f-303">Закройте окно Параметры построения.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="0ee0f-304">Сохраните сцену и проекта (**ФАЙЛ > Сохранить СЦЕНУ / FILE > Сохранить ПРОЕКТ**).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="0ee0f-305">Глава 5 – Настройка камеры</span><span class="sxs-lookup"><span data-stu-id="0ee0f-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0ee0f-306">Если вы хотите пропустить *Настройка Unity* компонент курс и по-прежнему непосредственно в код, вы можете загрузить [Azure MR-312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), импортировать его в проект в качестве [ **Пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжить из [Глава 7](#chapter-7-–-create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="0ee0f-307">В *панели иерархии*выберите **Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="0ee0f-308">После выбора можно видеть все компоненты **Main Camera** в *панели Инспектора*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="0ee0f-309">**Объекта Camera** должен иметь имя **Main Camera** (Обратите внимание, правильность написания)</span><span class="sxs-lookup"><span data-stu-id="0ee0f-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="0ee0f-310">Main Camera **тега** должно быть присвоено **MainCamera** (Обратите внимание, правильность написания)</span><span class="sxs-lookup"><span data-stu-id="0ee0f-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="0ee0f-311">Убедитесь, что **преобразование положения** присваивается **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="0ee0f-312">Задайте **очистить флаги** для **Одноцветная**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="0ee0f-313">Задайте **фона** цвет компонента камеры для **черная, альфа-значение 0 (шестнадцатеричный код: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![Настройка камеры](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="0ee0f-315">Глава 6 – импорт библиотеки Newtonsoft</span><span class="sxs-lookup"><span data-stu-id="0ee0f-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="0ee0f-316">Для десериализации и сериализации объектов получаемых и отправляемых в службу программ-роботов необходимо скачать **Newtonsoft** библиотеки.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="0ee0f-317">Вы найдете [совместимой версии, уже упорядочены с правильного Unity структуре папок здесь](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="0ee0f-318">Чтобы импортировать библиотеки Newtonsoft в проект, используйте пакет Unity, который прилагается этот курс.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="0ee0f-319">Добавить *.unitypackage* к Unity с помощью **активы** > **Импорт пакета** > **пользовательского пакета** пункт меню.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Импортировать библиотеку Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="0ee0f-321">В **Импорт пакета Unity** который появится убедитесь, что все, что в разделе (вплоть до) **подключаемые модули** выбран.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Импортировать библиотеку Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="0ee0f-323">Нажмите кнопку **импорта** кнопку, чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="0ee0f-324">Перейдите к **Newtonsoft** папке **подключаемые модули** в представлении проекта и выберите подключаемый модуль Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="0ee0f-325">С помощью подключаемого модуля Newtonsoft выбран, убедитесь, что **Any платформы** — **unchecked**, убедитесь, что флажок **WSAPlayer** также **unchecked**, Нажмите кнопку **применить**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="0ee0f-326">Это, чтобы убедиться, что файлы настроены правильно.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="0ee0f-327">Пометка этих подключаемых модулей позволяет настроить их только для использования в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="0ee0f-328">Существует другой набор их в папке WSA, которая будет использоваться после проект будет экспортирован из Unity.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="0ee0f-329">Затем необходимо открыть **WSA** папку, в пределах **Newtonsoft** папки.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="0ee0f-330">Вы увидите копию тот же файл, который вы только что настроили.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="0ee0f-331">Выберите файл и затем в инспекторе, убедитесь, что</span><span class="sxs-lookup"><span data-stu-id="0ee0f-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="0ee0f-332">**Любой платформе** является **unchecked**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="0ee0f-333">**только** **WSAPlayer** является **проверки**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="0ee0f-334">**Не обрабатывать** является **проверки**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="0ee0f-335">Глава 7 – создание BotTag</span><span class="sxs-lookup"><span data-stu-id="0ee0f-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="0ee0f-336">Создайте новый **тега** объект под названием **BotTag**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="0ee0f-337">Выберите Main Camera в сцене.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="0ee0f-338">Щелкните тег раскрывающегося меню на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="0ee0f-339">Щелкните **добавьте тег**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-339">Click on **Add Tag**.</span></span>

    ![Настройка камеры](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="0ee0f-341">Щелкните **+** символов.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-341">Click on the **+** symbol.</span></span> <span data-ttu-id="0ee0f-342">Имя нового **тега** как **BotTag**, *Сохранить*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![Настройка камеры](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="0ee0f-344">**Не** применить **BotTag** к камере Main.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="0ee0f-345">Если вы случайно сделали это, не забудьте заменить Main Camera, тег обратно в *MainCamera*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="0ee0f-346">Глава 8 – создать класс BotObjects</span><span class="sxs-lookup"><span data-stu-id="0ee0f-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="0ee0f-347">Первый скрипт, чтобы создать **BotObjects** класс, который является пустым классом создан таким образом, чтобы ряд других объектов класса, которые могут храниться в тот же сценарий и доступны для других сценариев в сцене.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="0ee0f-348">Создание этого класса является чисто архитектуры выбором, эти объекты могут быть размещены вместо этого в скрипт программ-роботов, который вы создадите далее в этом курсе.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="0ee0f-349">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-349">To create this class:</span></span> 

1.  <span data-ttu-id="0ee0f-350">Щелкните правой кнопкой мыши в *панель проекта*, затем **Создать > Папка**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="0ee0f-351">Назовите папку **сценариев**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-351">Name the folder **Scripts**.</span></span> 

    ![Создайте папку scripts.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="0ee0f-353">Дважды щелкните **сценариев** папку, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="0ee0f-354">Затем в этой папке, щелкните правой кнопкой мыши и выберите **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="0ee0f-355">Назовите сценарий **BotObjects**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="0ee0f-356">Дважды щелкните новый **BotObjects** скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="0ee0f-357">Удалите содержимое скрипта и замените его следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="0ee0f-358">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="0ee0f-359">Глава 9 – создать класс GazeInput</span><span class="sxs-lookup"><span data-stu-id="0ee0f-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="0ee0f-360">Далее нужно создать класс является **GazeInput** класса.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="0ee0f-361">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-361">This class is responsible for:</span></span>

- <span data-ttu-id="0ee0f-362">Создается курсор, который будет представлять *помощи* проигрывателя.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="0ee0f-363">Обнаружение объектов попадания по взглядом проигрывателя и содержит ссылку на обнаруженных объектов.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="0ee0f-364">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-364">To create this class:</span></span> 

1.  <span data-ttu-id="0ee0f-365">Перейдите к **сценариев** папку, созданную ранее.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="0ee0f-366">Щелкните правой кнопкой мыши внутри папки **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="0ee0f-367">Вызовите сценарий **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="0ee0f-368">Дважды щелкните новый **GazeInput** скрипт, чтобы открыть его с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="0ee0f-369">Вставьте следующую строку прямо на вверху имя класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="0ee0f-370">Затем добавьте следующие переменные внутри **GazeInput** класса выше **Start()** метод:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="0ee0f-371">Код для **Start()** метода должны быть добавлены.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="0ee0f-372">Вызывается при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="0ee0f-373">Реализуйте метод, который будет создать и настроить курсор взглядом:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="0ee0f-374">Реализуйте методы, которые позволят настроить Raycast из Main Camera и будет отслеживать фокус текущего объекта.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="0ee0f-375">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="0ee0f-376">Глава 10 – создать класс программ-роботов</span><span class="sxs-lookup"><span data-stu-id="0ee0f-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="0ee0f-377">Этот сценарий, который вы собираетесь создать теперь называется **программ-роботов**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="0ee0f-378">Это основной класс приложения, он сохраняет:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="0ee0f-379">Учетные данные программ-роботов приложение Web</span><span class="sxs-lookup"><span data-stu-id="0ee0f-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="0ee0f-380">Метод, который собирает голосовые команды пользователя</span><span class="sxs-lookup"><span data-stu-id="0ee0f-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="0ee0f-381">Метод, необходимо инициировать диалог с Ботом Web App</span><span class="sxs-lookup"><span data-stu-id="0ee0f-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="0ee0f-382">Метод, необходимые для отправки сообщений в веб приложение бота</span><span class="sxs-lookup"><span data-stu-id="0ee0f-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="0ee0f-383">Для отправки сообщений в службу программ-роботов, **SendMessageToBot()** сопрограммы построит действие, которое является объектом, Bot Framework распознает как данные, отправляемые пользователем.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="0ee0f-384">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-384">To create this class:</span></span> 

1. <span data-ttu-id="0ee0f-385">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="0ee0f-386">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="0ee0f-387">Назовите сценарий **программ-роботов**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="0ee0f-388">Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="0ee0f-389">Обновите пространства имен должны совпадать, как показано ниже, в верхней части **программ-роботов** класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="0ee0f-390">Внутри **программ-роботов** класса добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="0ee0f-391">Убедитесь, что вы вставляете вашей **программ-роботов секретный ключ** в **botSecret** переменной.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="0ee0f-392">Будет записанными вашей **программ-роботов секретный ключ** в начале этого курса в  **[Глава 2](#chapter-2---create-the-azure-bot-service), шаг 10**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="0ee0f-393">Код для **Awake()** и **Start()** теперь должен быть добавлен.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="0ee0f-394">Добавление двух обработчиков, которые называются библиотеками речи, когда записи голоса начинается и заканчивается.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="0ee0f-395">*DictationRecognizer* автоматически останавливаются записи голоса пользователя, когда пользователь останавливает кстати.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="0ee0f-396">Следующий обработчик собирает результат голосовой ввод пользователя и вызывает сопрограммы, отвечающего за отправку сообщения программ-роботов приложение веб-службы.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="0ee0f-397">Следующие сопрограммы называется мог начать диалог с Ботом.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="0ee0f-398">Обратите внимание, что после завершения вызова диалога, вызовет **SendMessageToCoroutine()** путем передачи ряда параметров, которые будут задавать действия для отправки в службу программ-роботов, как пустое сообщение.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="0ee0f-399">Это позволяет запрашивать службу программ-роботов, инициировать диалог.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="0ee0f-400">Следующие сопрограммы вызывается для создания действий, отправляемых в службу программ-роботов.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="0ee0f-401">Следующие сопрограммы вызывается для запроса ответа после отправки действие службу программ-роботов.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="0ee0f-402">Последний метод для добавления в этот класс необходим для отображения сообщения в сцене:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="0ee0f-403">Может появиться ошибка консоли редактора Unity, об отсутствующих **SceneOrganiser** класса.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="0ee0f-404">Игнорируйте это сообщение, так как позже в этом руководстве вы создадите этот класс.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="0ee0f-405">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="0ee0f-406">Глава 11 — создать класс взаимодействия</span><span class="sxs-lookup"><span data-stu-id="0ee0f-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="0ee0f-407">Вы собираетесь создать класс теперь называется **взаимодействия**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="0ee0f-408">Этот класс используется для обнаружения HoloLens коснитесь входные данные пользователя.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="0ee0f-409">Если пользователь касается просматривая *программ-роботов* объект в сцене и бота готов для прослушивания речевой ввод, меняет цвет для объекта программ-роботов **red** и начать прослушивание речевой ввод.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="0ee0f-410">Этот класс наследует от **GazeInput** класса и поэтому является возможность создания ссылок на **Start()** метод и переменные из этого класса, обозначенное с помощью **базового**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="0ee0f-411">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-411">To create this class:</span></span>

1.  <span data-ttu-id="0ee0f-412">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="0ee0f-413">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="0ee0f-414">Назовите сценарий **взаимодействия**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="0ee0f-415">Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="0ee0f-416">Обновление пространства имен и наследование классов должны совпадать, как показано ниже, в верхней части **взаимодействия** класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="0ee0f-417">Внутри **взаимодействия** класса добавьте следующую переменную:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="0ee0f-418">Затем добавьте **Start()** метод:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="0ee0f-419">Добавьте обработчик, который будет применяться при выполнении пользователем жеста касания HoloLens камеры</span><span class="sxs-lookup"><span data-stu-id="0ee0f-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="0ee0f-420">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="0ee0f-421">Глава 12 — создать класс SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="0ee0f-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="0ee0f-422">В этом лабораторном занятии требуется последний класс называется **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="0ee0f-423">Этот класс настроит сцены программно, путем добавления компонентов и сценариев Main Camera и создания соответствующих объектов в сцене.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="0ee0f-424">Для создания этого класса:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-424">To create this class:</span></span>

1.  <span data-ttu-id="0ee0f-425">Дважды щелкните **сценариев** папки, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="0ee0f-426">Щелкните правой кнопкой мыши внутри **сценарии** папку, нажмите кнопку **Создать > C# сценарий**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="0ee0f-427">Назовите сценарий **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="0ee0f-428">Дважды щелкните новый скрипт, чтобы открыть его с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="0ee0f-429">Внутри **SceneOrganiser** класса добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="0ee0f-430">Затем добавьте **Awake()** и **Start()** методы:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="0ee0f-431">Добавьте следующий метод, отвечает за создание программ-роботов объект в сцене и настройка параметров и компонентов:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="0ee0f-432">Добавьте следующий метод, отвечает за создание объект пользовательского интерфейса в сцене, представляющий ответы от программ-роботов:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="0ee0f-433">Не забудьте сохранить изменения в *Visual Studio* перед возвратом *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="0ee0f-434">В редакторе Unity перетащите **SceneOrganiser** сценарий из папки скриптов Main Camera.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="0ee0f-435">Компонент Organiser сцены должен появиться в объекте Main Camera, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="0ee0f-437">Глава 13 – перед сборкой</span><span class="sxs-lookup"><span data-stu-id="0ee0f-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="0ee0f-438">Для выполнения полной проверки приложения необходимо будет загружать неопубликованные его на ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="0ee0f-439">Прежде чем сделать, убедитесь, что:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="0ee0f-440">Все параметры, упомянутые в [ **Глава 4** ](#Chapter-4-–-Set-up-the-unity-project) заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="0ee0f-441">Сценарий **SceneOrganiser** присоединяется к **Main Camera** объекта.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="0ee0f-442">В **программ-роботов** класса, убедитесь, что вы вставили вашей **программ-роботов секретный ключ** в **botSecret** переменной.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="0ee0f-443">Глава 14 — сборки и передайте в HoloLens</span><span class="sxs-lookup"><span data-stu-id="0ee0f-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="0ee0f-444">Все необходимое для раздела этого проекта Unity теперь завершен, так что наступило время создавать его с Unity.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="0ee0f-445">Перейдите к **параметры сборки**, **файл > Параметры сборки...** .</span><span class="sxs-lookup"><span data-stu-id="0ee0f-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="0ee0f-446">Из **параметры построения** окно, нажмите кнопку **построения**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Создание приложения из Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="0ee0f-448">Если не сделали, установите **Unity C# проекты**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="0ee0f-449">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-449">Click **Build**.</span></span> <span data-ttu-id="0ee0f-450">Unity приведет к запуску **проводнике** окно, где необходимо создать, а затем выберите папку, чтобы создать приложение в.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="0ee0f-451">Создайте эту папку и назовите его **приложения**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="0ee0f-452">Затем с помощью **приложения** щелкните папку, **Выбор папки**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="0ee0f-453">Unity начнется построение проекта для **приложения** папки.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="0ee0f-454">Один раз Unity завершил построение (может занять некоторое время), он будет открыт **проводнике** окне в местоположении, построения (проверьте панели задач, так как он может не всегда отображаются над windows, но уведомит вас о Добавление нового окно).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="0ee0f-455">Глава 15 – развертывание в HoloLens</span><span class="sxs-lookup"><span data-stu-id="0ee0f-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="0ee0f-456">Для развертывания на HoloLens:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="0ee0f-457">Вам потребуется IP-адрес вашего HoloLens (для удаленного развертывания), а для обеспечения вашей HoloLens, находится в **режим разработчика**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="0ee0f-458">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-458">To do this:</span></span>

    1. <span data-ttu-id="0ee0f-459">Хотя носить вашей HoloLens, откройте **параметры**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="0ee0f-460">Перейдите к **сеть и Интернет > Wi-Fi > Дополнительные параметры**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="0ee0f-461">Примечание **IPv4** адрес.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="0ee0f-462">Затем перейдите к **параметры**, а затем в **обновление и безопасность > для разработчиков**</span><span class="sxs-lookup"><span data-stu-id="0ee0f-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="0ee0f-463">Включен режим разработчика.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="0ee0f-464">Перейдите к новой сборки Unity ( **приложения** папки) и откройте файл решения с **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="0ee0f-465">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="0ee0f-466">В **платформа решения**выберите **x86**, **удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Разверните решение в Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="0ee0f-468">Перейдите к **меню "сборка"** и щелкнуть **развернуть решение**, чтобы загрузить неопубликованное приложение для вашего HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="0ee0f-469">Приложения должны появиться в списке установленных приложений на HoloLens, Готово к запуску!</span><span class="sxs-lookup"><span data-stu-id="0ee0f-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="0ee0f-470">Чтобы развернуть иммерсивных гарнитура, переключите **платформа решения** для *локального компьютера*и задайте **конфигурации** для *Отладка*, с *x86* как **платформы**.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="0ee0f-471">Затем развернуть на локальный компьютер, с помощью **меню "сборка"**, выбрав *развернуть решение*.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="0ee0f-472">Глава 16 – с помощью приложения на HoloLens</span><span class="sxs-lookup"><span data-stu-id="0ee0f-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="0ee0f-473">Сразу после запуска приложения, вы увидите бота как синий сферы перед глазами.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="0ee0f-474">Используйте **коснитесь жест** хотя gazing в сферу, чтобы начать диалог.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="0ee0f-475">Ожидания для диалога для запуска (пользовательского интерфейса будет выведено сообщение, когда это случается).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="0ee0f-476">После получения вводное сообщение от программ-роботов, снова коснитесь на бота, он будет красным цветом и начать прослушивание ваш голос.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="0ee0f-477">После остановки разговор, приложение будет отправлять сообщения боту, и вы своевременно получите ответ, который будет отображаться в пользовательском Интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="0ee0f-478">Повторите процедуру, чтобы отправлять дополнительные сообщения бота (необходимо коснитесь каждый раз, когда вы хотите отправить сообщение).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="0ee0f-479">Этот диалог показано, как Bot можно сохранить сведения (имя), пока также обеспечение известные данные (например, элементы на складе).</span><span class="sxs-lookup"><span data-stu-id="0ee0f-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="0ee0f-480">Некоторые вопросы, которые можете попросить бота:</span><span class="sxs-lookup"><span data-stu-id="0ee0f-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="0ee0f-481">Готового приложения Web App программ-роботов (версия 4)</span><span class="sxs-lookup"><span data-stu-id="0ee0f-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="0ee0f-482">Поздравляем, вы создали приложение смешанной реальности, использующем присоединение к Azure Web App, программ-роботов, Microsoft Bot Framework версии 4.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Конечный продукт](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="0ee0f-484">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="0ee0f-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="0ee0f-485">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="0ee0f-485">Exercise 1</span></span>

<span data-ttu-id="0ee0f-486">Структура диалога в этой лабораторной работе является очень простым.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="0ee0f-487">Используйте Microsoft LUIS для Наделите своего бота возможности распознавания естественного языка.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="0ee0f-488">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="0ee0f-488">Exercise 2</span></span>

<span data-ttu-id="0ee0f-489">В этом примере не поддерживает завершение диалога и его перезапуск.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="0ee0f-490">Чтобы сделать программ-роботов, функцию завершения, попробуйте реализовать закрытия для диалога.</span><span class="sxs-lookup"><span data-stu-id="0ee0f-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
