---
title: MR и Azure 312 — интеграция с Bot
description: Пройдите этот курс, чтобы научиться создавать и развертывать роботы, использовать Microsoft Bot Framework v4 и взаимодействовать с ней в приложении для смешанной реальности.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, учебник, API, компьютерное зрение, hololens, иммерсивное, VR, Microsoft Bot Framework V4, Bot веб-приложения, Bot Framework, Microsoft Bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63542466"
---
>[!NOTE]
><span data-ttu-id="b5327-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b5327-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b5327-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="b5327-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b5327-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b5327-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b5327-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="b5327-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b5327-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b5327-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b5327-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="b5327-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="b5327-110">MR и Azure 312: Интеграция с Bot</span><span class="sxs-lookup"><span data-stu-id="b5327-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="b5327-111">В этом курсе вы узнаете, как создать и развернуть робот с помощью Microsoft Bot Framework v4 и взаимодействовать с ним через приложение Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b5327-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="b5327-112">**Microsoft Bot Framework v4** — это набор интерфейсов API, предназначенных для предоставления разработчикам средств для создания расширяемого и масштабируемого приложения-робота.</span><span class="sxs-lookup"><span data-stu-id="b5327-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="b5327-113">Дополнительные сведения см. на [странице Microsoft Bot Framework](https://dev.botframework.com/) или в [репозитории Git v4](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="b5327-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="b5327-114">После завершения этого курса вы получите приложение Windows Mixed Reality, которое сможет сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="b5327-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="b5327-115">Используйте **жест касания** для запуска программы-робота, ожидающей голоса пользователя.</span><span class="sxs-lookup"><span data-stu-id="b5327-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="b5327-116">Когда пользователь сказал что-то, программа Bot попытается предоставить ответ.</span><span class="sxs-lookup"><span data-stu-id="b5327-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="b5327-117">Отображение ответа программы-роботы в виде текста, расположенного рядом с Bot, в сцене Unity.</span><span class="sxs-lookup"><span data-stu-id="b5327-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="b5327-118">В приложении вы будете выполнять интеграцию результатов с вашей структурой.</span><span class="sxs-lookup"><span data-stu-id="b5327-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="b5327-119">Этот курс предназначен для изучения того, как интегрировать службу Azure с проектом Unity.</span><span class="sxs-lookup"><span data-stu-id="b5327-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="b5327-120">Это ваша задача использовать знания, полученные из этого курса, для улучшения приложения смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b5327-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="b5327-121">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="b5327-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b5327-122">Хождение</span><span class="sxs-lookup"><span data-stu-id="b5327-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b5327-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b5327-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b5327-124"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="b5327-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b5327-125">MR и Azure 312: Интеграция с Bot</span><span class="sxs-lookup"><span data-stu-id="b5327-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="b5327-126">✔️</span><span class="sxs-lookup"><span data-stu-id="b5327-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b5327-127">✔️</span><span class="sxs-lookup"><span data-stu-id="b5327-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b5327-128">Хотя этот курс в основном ориентирован на HoloLens, вы можете также применить сведения, которые вы узнаете в этом курсе, к головным телефонам Windows Mixed Reality (VR).</span><span class="sxs-lookup"><span data-stu-id="b5327-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="b5327-129">Так как у головных гарнитур нет доступных камер, вам потребуется внешняя камера, подключенная к компьютеру.</span><span class="sxs-lookup"><span data-stu-id="b5327-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="b5327-130">При работе с курсом вы увидите заметки о любых изменениях, которые могут потребоваться для поддержки головных телефонов (VR).</span><span class="sxs-lookup"><span data-stu-id="b5327-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5327-131">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="b5327-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b5327-132">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Unity и C#.</span><span class="sxs-lookup"><span data-stu-id="b5327-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b5327-133">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018).</span><span class="sxs-lookup"><span data-stu-id="b5327-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="b5327-134">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="b5327-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="b5327-135">Для этого курса рекомендуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="b5327-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b5327-136">ПК для разработки, [совместимый с Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) для разработки головных телефонов (VR)</span><span class="sxs-lookup"><span data-stu-id="b5327-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b5327-137">Windows 10 для дизайнеров с обновлением (или более поздней версии) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="b5327-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b5327-138">Последний пакет SDK для Windows 10</span><span class="sxs-lookup"><span data-stu-id="b5327-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b5327-139">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="b5327-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b5327-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b5327-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="b5327-141">Высокодоступная [гарнитура Windows Mixed Reality (VR)](immersive-headset-hardware-details.md) или [Microsoft HoloLens](hololens-hardware-details.md) с включенным режимом разработчика</span><span class="sxs-lookup"><span data-stu-id="b5327-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b5327-142">Доступ к Интернету для Azure и получение Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="b5327-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="b5327-143">Для получения дополнительных сведений [перейдите по этой ссылке](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="b5327-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="b5327-144">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="b5327-144">Before you start</span></span>

1.  <span data-ttu-id="b5327-145">Чтобы избежать проблем при создании этого проекта, настоятельно рекомендуется создать проект, упомянутый в этом руководстве, в корневой или ближайшем к корневой папке (длинные пути к папкам могут вызвать проблемы во время сборки).</span><span class="sxs-lookup"><span data-stu-id="b5327-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="b5327-146">Настройка и тестирование HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5327-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="b5327-147">Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="b5327-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="b5327-148">Рекомендуется выполнять настройку калибровки и датчика при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="b5327-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="b5327-149">Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="b5327-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="b5327-150">Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="b5327-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="b5327-151">Глава 1. Создание приложения-робота</span><span class="sxs-lookup"><span data-stu-id="b5327-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="b5327-152">Первым шагом является создание программы Bot в качестве локального веб-приложения ASP.Net Core.</span><span class="sxs-lookup"><span data-stu-id="b5327-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="b5327-153">После завершения и тестирования вы сможете опубликовать его на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="b5327-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="b5327-154">Откройте Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5327-154">Open Visual Studio.</span></span> <span data-ttu-id="b5327-155">Создайте новый проект, выберите в качестве типа проекта **веб-приложение ASP NET Core** (его можно найти в подразделе .NET Core) и вызовите его **мибот**.</span><span class="sxs-lookup"><span data-stu-id="b5327-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="b5327-156">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="b5327-156">Click **OK**.</span></span>

2.  <span data-ttu-id="b5327-157">В окне, которое будет отображаться, выберите пустое.</span><span class="sxs-lookup"><span data-stu-id="b5327-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="b5327-158">Также убедитесь, что для целевого объекта задано значение **ASP NET Core 2,0** , а для параметра Проверка подлинности — значение **без проверки**подлинности.</span><span class="sxs-lookup"><span data-stu-id="b5327-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="b5327-159">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="b5327-159">Click **OK**.</span></span>  

    ![Создание приложения-робота](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="b5327-161">Теперь решение откроется.</span><span class="sxs-lookup"><span data-stu-id="b5327-161">The solution will now open.</span></span> <span data-ttu-id="b5327-162">Щелкните правой кнопкой мыши решение **мибот** в **Обозреватель решений** и выберите пункт **Управление пакетами NuGet для решения**.</span><span class="sxs-lookup"><span data-stu-id="b5327-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Создание приложения-робота](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="b5327-164">На вкладке **Обзор** выполните поиск **Microsoft. Bot. Builder. Integration. AspNet. Core** (убедитесь, что установлен флажок **Предварительная версия включена** ).</span><span class="sxs-lookup"><span data-stu-id="b5327-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="b5327-165">Выберите версию пакета **4.0.1-Preview**и установите флажки в полях проекта.</span><span class="sxs-lookup"><span data-stu-id="b5327-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="b5327-166">Затем нажмите кнопку **установить**.</span><span class="sxs-lookup"><span data-stu-id="b5327-166">Then click on **Install**.</span></span> <span data-ttu-id="b5327-167">Теперь вы установили библиотеки, необходимые для **Bot Framework v4**.</span><span class="sxs-lookup"><span data-stu-id="b5327-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="b5327-168">Закройте страницу NuGet.</span><span class="sxs-lookup"><span data-stu-id="b5327-168">Close the NuGet page.</span></span>

    ![Создание приложения-робота](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="b5327-170">Щелкните правой кнопкой мыши *проект* **мибот**в **Обозреватель решений** и выберите **Добавить** **|** **класс**.</span><span class="sxs-lookup"><span data-stu-id="b5327-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Создание приложения-робота](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="b5327-172">Назовите класс **мибот** и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="b5327-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Создание приложения-робота](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="b5327-174">Повторите предыдущую точку, чтобы создать другой класс с именем **конверсатионконтекст**.</span><span class="sxs-lookup"><span data-stu-id="b5327-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="b5327-175">Щелкните правой кнопкой мыши узел **wwwroot** в **Обозреватель решений** и выберите команду **добавить** **|** **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="b5327-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="b5327-176">Выберите **HTML-страница** (она будет находиться в подразделе веб).</span><span class="sxs-lookup"><span data-stu-id="b5327-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="b5327-177">Назовите файл **Default. HTML**.</span><span class="sxs-lookup"><span data-stu-id="b5327-177">Name the file **default.html**.</span></span> <span data-ttu-id="b5327-178">Нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="b5327-178">Click **Add**.</span></span>

    ![Создание приложения-робота](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="b5327-180">Список классов и объектов в **Обозреватель решений** должен выглядеть, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="b5327-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Создание приложения-робота](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="b5327-182">Дважды щелкните класс **конверсатионконтекст** .</span><span class="sxs-lookup"><span data-stu-id="b5327-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="b5327-183">Этот класс отвечает за хранение переменных, используемых программой Bot для поддержания контекста диалога.</span><span class="sxs-lookup"><span data-stu-id="b5327-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="b5327-184">Эти значения контекста диалога сохраняются в экземпляре этого класса, так как любой экземпляр класса **мибот** будет обновляться при каждом получении действия.</span><span class="sxs-lookup"><span data-stu-id="b5327-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="b5327-185">Добавьте в класс следующий код:</span><span class="sxs-lookup"><span data-stu-id="b5327-185">Add the following code to the class:</span></span>

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

11. <span data-ttu-id="b5327-186">Дважды щелкните класс **мибот** .</span><span class="sxs-lookup"><span data-stu-id="b5327-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="b5327-187">Этот класс будет размещать обработчики, вызываемые любыми входящими действиями от клиента.</span><span class="sxs-lookup"><span data-stu-id="b5327-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="b5327-188">В этом классе будет добавлен код, используемый для создания диалога между Bot и клиентом.</span><span class="sxs-lookup"><span data-stu-id="b5327-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="b5327-189">Как упоминалось ранее, экземпляр этого класса инициализируется каждый раз при получении действия.</span><span class="sxs-lookup"><span data-stu-id="b5327-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="b5327-190">Добавьте в этот класс следующий код:</span><span class="sxs-lookup"><span data-stu-id="b5327-190">Add the following code to this class:</span></span>

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

12. <span data-ttu-id="b5327-191">Дважды щелкните класс **Startup** .</span><span class="sxs-lookup"><span data-stu-id="b5327-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="b5327-192">Этот класс инициализирует робот.</span><span class="sxs-lookup"><span data-stu-id="b5327-192">This class will initialize the bot.</span></span> <span data-ttu-id="b5327-193">Добавьте в класс следующий код:</span><span class="sxs-lookup"><span data-stu-id="b5327-193">Add the following code to the class:</span></span>

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

13. <span data-ttu-id="b5327-194">Откройте файл класса **Program** и проверьте, что код в нем совпадает со следующим:</span><span class="sxs-lookup"><span data-stu-id="b5327-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

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

14. <span data-ttu-id="b5327-195">Не забудьте сохранить изменения. чтобы сделать это, выберите **файл** > **сохранить все**на панели инструментов в верхней части Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5327-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="b5327-196">Глава 2. Создание службы Azure Bot</span><span class="sxs-lookup"><span data-stu-id="b5327-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="b5327-197">Теперь, когда вы создали код для программы Bot, необходимо опубликовать его в экземпляре службы *веб-приложения Bot* на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="b5327-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="b5327-198">В этой главе мы покажем, как создать и настроить службу Bot в Azure, а затем опубликовать в ней свой код.</span><span class="sxs-lookup"><span data-stu-id="b5327-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="b5327-199">Сначала войдите на портал Azure (https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="b5327-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="b5327-200">Если у вас еще нет учетной записи Azure, необходимо создать ее.</span><span class="sxs-lookup"><span data-stu-id="b5327-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b5327-201">Если вы используете этот учебник в учебной или лабораторной ситуации, обратитесь к своему преподавателю или к одной из прокторс, чтобы получить помощь в настройке новой учетной записи.</span><span class="sxs-lookup"><span data-stu-id="b5327-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="b5327-202">После входа в систему щелкните **создать ресурс** в левом верхнем углу, а затем выполните поиск по запросу *Bot веб-приложения*и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="b5327-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="b5327-204">На новой странице будет представлено описание службы *веб-приложения Bot* .</span><span class="sxs-lookup"><span data-stu-id="b5327-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="b5327-205">В нижнем левом углу этой страницы нажмите кнопку **создать** , чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="b5327-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="b5327-207">После нажатия кнопки **создать**:</span><span class="sxs-lookup"><span data-stu-id="b5327-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="b5327-208">Вставьте нужное **имя** для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="b5327-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="b5327-209">Выберите **подписку**.</span><span class="sxs-lookup"><span data-stu-id="b5327-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="b5327-210">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="b5327-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="b5327-211">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="b5327-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b5327-212">Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b5327-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="b5327-213">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, [перейдите по этой ссылке.](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="b5327-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="b5327-214">Определите расположение группы ресурсов (при создании новой группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="b5327-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="b5327-215">В идеале это расположение будет находиться в регионе, в котором будет выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="b5327-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="b5327-216">Некоторые ресурсы Azure доступны только в определенных регионах.</span><span class="sxs-lookup"><span data-stu-id="b5327-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="b5327-217">Выберите **ценовую категорию** , подходящую для вас. Если вы впервые создаете службу *веб-приложения Bot* , для вас должен быть доступен бесплатный уровень (с именем F0).</span><span class="sxs-lookup"><span data-stu-id="b5327-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="b5327-218">**Имя приложения** может быть просто оставлено *именем Bot*.</span><span class="sxs-lookup"><span data-stu-id="b5327-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="b5327-219">Оставьте *шаблон Bot* **Basic (C#)** .</span><span class="sxs-lookup"><span data-stu-id="b5327-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="b5327-220">*План службы приложений или расположение* должны быть заполнены автоматически для вашей учетной записи.</span><span class="sxs-lookup"><span data-stu-id="b5327-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="b5327-221">Укажите службу **хранилища Azure** , которую вы хотите использовать для размещения программы-робота.</span><span class="sxs-lookup"><span data-stu-id="b5327-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="b5327-222">Если у вас его еще нет, его можно создать здесь.</span><span class="sxs-lookup"><span data-stu-id="b5327-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="b5327-223">Также необходимо подтвердить, что вы поняли условия, примененные к этой службе.</span><span class="sxs-lookup"><span data-stu-id="b5327-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="b5327-224">Нажмите кнопку Создать.</span><span class="sxs-lookup"><span data-stu-id="b5327-224">Click Create.</span></span>
 
        ![Создание службы Azure Bot](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="b5327-226">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="b5327-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="b5327-227">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="b5327-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="b5327-229">Щелкните уведомление, чтобы просмотреть новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="b5327-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="b5327-231">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="b5327-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="b5327-232">Вы будете перенаправлены на новый экземпляр службы Azure.</span><span class="sxs-lookup"><span data-stu-id="b5327-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="b5327-234">На этом этапе необходимо настроить функцию **прямой командной строки** , которая позволит клиентскому приложению взаимодействовать с этой службой Bot.</span><span class="sxs-lookup"><span data-stu-id="b5327-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="b5327-235">Щелкните **каналы**, а затем в разделе **Добавление избранного канала** щелкните **настроить прямой канал линии**.</span><span class="sxs-lookup"><span data-stu-id="b5327-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="b5327-237">На этой странице находятся **секретные ключи** , которые позволяют клиентскому приложению проходить проверку подлинности с помощью программы-робота.</span><span class="sxs-lookup"><span data-stu-id="b5327-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="b5327-238">Нажмите кнопку **Показать** и получите копию одного из отображаемых ключей, так как это потребуется позже в проекте.</span><span class="sxs-lookup"><span data-stu-id="b5327-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="b5327-240">Глава 3. Публикация программы-робота в службе Azure Web App Bot</span><span class="sxs-lookup"><span data-stu-id="b5327-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="b5327-241">Теперь, когда служба готова, необходимо опубликовать созданный ранее код Bot в созданной службе веб-приложения Bot.</span><span class="sxs-lookup"><span data-stu-id="b5327-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="b5327-242">Каждый раз при внесении изменений в решение или код для программы-робота потребуется опубликовать программу Bot в службе Azure.</span><span class="sxs-lookup"><span data-stu-id="b5327-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="b5327-243">Вернитесь к созданному ранее решению Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5327-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="b5327-244">Щелкните правой кнопкой мыши проект **мибот** в **Обозреватель решений**, а затем щелкните **Publish (опубликовать**).</span><span class="sxs-lookup"><span data-stu-id="b5327-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Публикация программы Bot в службе веб-приложения Azure Bot](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="b5327-246">На странице *Выбор целевого объекта публикации* щелкните **служба приложений**, а затем **выберите существующий**, в последний раз щелкните **создать профиль** (если это не отображается, может потребоваться щелкнуть стрелку раскрывающегося списка рядом с кнопкой *опубликовать* .)</span><span class="sxs-lookup"><span data-stu-id="b5327-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Публикация программы Bot в службе веб-приложения Azure Bot](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="b5327-248">Если вы еще не вошли в учетную запись Майкрософт, это можно сделать здесь.</span><span class="sxs-lookup"><span data-stu-id="b5327-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="b5327-249">На странице **Публикация** вам нужно будет задать ту же подписку, которая  использовалась для создания службы *веб-приложения Bot* .</span><span class="sxs-lookup"><span data-stu-id="b5327-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="b5327-250">Затем задайте **представление** в качестве **группы ресурсов** и в раскрывающейся структуре папок выберите **группу ресурсов** , созданную ранее.</span><span class="sxs-lookup"><span data-stu-id="b5327-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="b5327-251">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="b5327-251">Click **OK**.</span></span> 

    ![Публикация программы Bot в службе веб-приложения Azure Bot](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="b5327-253">Теперь нажмите кнопку " **опубликовать** " и дождитесь публикации программы-робота (это может занять несколько минут).</span><span class="sxs-lookup"><span data-stu-id="b5327-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Публикация программы Bot в службе веб-приложения Azure Bot](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="b5327-255">Глава 4 — Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="b5327-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="b5327-256">Ниже приведена типичная Настройка для разработки с использованием смешанной реальности, которая является хорошим шаблоном для других проектов.</span><span class="sxs-lookup"><span data-stu-id="b5327-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b5327-257">Откройте *Unity* и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="b5327-257">Open *Unity* and click **New**.</span></span> 

    ![Настройка проекта Unity](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="b5327-259">Теперь необходимо указать имя проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="b5327-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="b5327-260">Вставьте **Hololens Bot**.</span><span class="sxs-lookup"><span data-stu-id="b5327-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="b5327-261">Убедитесь, что для шаблона проекта задано значение **3D**.</span><span class="sxs-lookup"><span data-stu-id="b5327-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="b5327-262">Задайте для **расположения нужное расположение** (Помните, что ближе к корневым каталогам лучше).</span><span class="sxs-lookup"><span data-stu-id="b5327-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b5327-263">Затем нажмите кнопку **создать проект**.</span><span class="sxs-lookup"><span data-stu-id="b5327-263">Then, click **Create project**.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="b5327-265">При открытом Unity стоит проверить, что для **редактора скриптов** по умолчанию задано значение **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b5327-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b5327-266">Перейдите к разделу **изменение параметров >** , а затем в новом окне перейдите к разделу **Внешние инструменты**.</span><span class="sxs-lookup"><span data-stu-id="b5327-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b5327-267">Измените **Редактор внешних скриптов** на **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="b5327-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b5327-268">Закройте окно **настройки** .</span><span class="sxs-lookup"><span data-stu-id="b5327-268">Close the **Preferences** window.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="b5327-270">Затем перейдите в раздел **файл > параметры сборки** и выберите **универсальная платформа Windows**, а затем нажмите кнопку **переключения платформы** , чтобы применить выбранные элементы.</span><span class="sxs-lookup"><span data-stu-id="b5327-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Настройка проекта Unity](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="b5327-272">Несмотря на то что в **файле > параметры сборки** , убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="b5327-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="b5327-273">**Целевое устройство** имеет значение **Hololens**</span><span class="sxs-lookup"><span data-stu-id="b5327-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="b5327-274">Для впечатляющих головных телефонов задайте для параметра **целевое устройство** *любое устройство*.</span><span class="sxs-lookup"><span data-stu-id="b5327-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="b5327-275">Для **типа сборки** задано значение **D3D**</span><span class="sxs-lookup"><span data-stu-id="b5327-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="b5327-276">**Пакет SDK** установлен в значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="b5327-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="b5327-277">Для **версии Visual Studio** установлено значение " **Последняя установка** "</span><span class="sxs-lookup"><span data-stu-id="b5327-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="b5327-278">**Сборка и запуск** настроены на **локальный компьютер**</span><span class="sxs-lookup"><span data-stu-id="b5327-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="b5327-279">Сохраните сцену и добавьте ее в сборку.</span><span class="sxs-lookup"><span data-stu-id="b5327-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="b5327-280">Для этого выберите **Добавить открытые сцены**.</span><span class="sxs-lookup"><span data-stu-id="b5327-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b5327-281">Появится окно сохранения.</span><span class="sxs-lookup"><span data-stu-id="b5327-281">A save window will appear.</span></span>
        
            ![Настройка проекта Unity](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="b5327-283">Создайте новую папку для этого, а также любой будущей сцены, а затем нажмите кнопку **создать папку** , чтобы создать новую папку, назовите ее « **сцены**».</span><span class="sxs-lookup"><span data-stu-id="b5327-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Настройка проекта Unity](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="b5327-285">Откройте созданную папку **сцены** , а затем в текстовом поле *имя файла*введите **Ботсцене**, а затем щелкните **Save (сохранить**).</span><span class="sxs-lookup"><span data-stu-id="b5327-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="b5327-287">Оставшиеся параметры, в **параметрах сборки**, должны быть оставлены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b5327-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="b5327-288">В окне *параметры сборки* нажмите кнопку **Параметры проигрывателя** , чтобы открыть связанную панель в пространстве, где находится *инспектор* .</span><span class="sxs-lookup"><span data-stu-id="b5327-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Настройка проекта Unity](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="b5327-290">На этой панели необходимо проверить несколько параметров:</span><span class="sxs-lookup"><span data-stu-id="b5327-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="b5327-291">На вкладке **другие параметры** выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b5327-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="b5327-292">**Версия среды выполнения сценариев** должна быть **экспериментальной (.NET 4,6 эквивалент)** ; чтобы изменить это, потребуется перезапустить редактор.</span><span class="sxs-lookup"><span data-stu-id="b5327-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="b5327-293">**Серверная часть сценариев** должна быть **.NET**</span><span class="sxs-lookup"><span data-stu-id="b5327-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="b5327-294">**Уровень совместимости API** должен быть **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="b5327-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="b5327-296">На вкладке **Параметры публикации** в разделе **возможности**установите флажок:</span><span class="sxs-lookup"><span data-stu-id="b5327-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="b5327-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b5327-297">**InternetClient**</span></span>
        - <span data-ttu-id="b5327-298">**Звук**</span><span class="sxs-lookup"><span data-stu-id="b5327-298">**Microphone**</span></span>

            ![Настройка проекта Unity](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="b5327-300">На более низких панели в **параметрах XR** (см. ниже **Параметры публикации**), **поддерживаемая виртуальная реальность**Tick, убедитесь, что добавлен **пакет SDK для Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="b5327-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Настройка проекта Unity](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="b5327-302">Назад в *параметрах сборки* проект _Unity C#_  больше не является серым. Установите флажок рядом с этим.</span><span class="sxs-lookup"><span data-stu-id="b5327-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="b5327-303">Закройте окно параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="b5327-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="b5327-304">Сохраните сцену и проект (**файл > сохранить сцену или файл > сохранить проект**).</span><span class="sxs-lookup"><span data-stu-id="b5327-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="b5327-305">Глава 5 — Настройка камеры</span><span class="sxs-lookup"><span data-stu-id="b5327-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5327-306">Если вы хотите пропустить компонент *установки Unity* , установленный в этом курсе, и продолжить работу с кодом, скачайте этот пакет [Azure-MR-312-Package. пакет unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), импортируйте его в проект в качестве [**пользовательского пакета**](https://docs.unity3d.com/Manual/AssetPackages.html), а затем продолжайте [ Глава 7](#chapter-7-–-create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="b5327-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="b5327-307">На *панели Иерархия*выберите **основную камеру**.</span><span class="sxs-lookup"><span data-stu-id="b5327-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="b5327-308">После выбора вы сможете увидеть все компоненты **основной камеры** на *панели инспектора*.</span><span class="sxs-lookup"><span data-stu-id="b5327-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="b5327-309">**Объект Camera** должен называться **основной камерой** (Обратите внимание на орфографию)</span><span class="sxs-lookup"><span data-stu-id="b5327-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="b5327-310">Для **тега** основной камеры необходимо задать значение **маинкамера** (Обратите внимание на орфографию)</span><span class="sxs-lookup"><span data-stu-id="b5327-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="b5327-311">Убедитесь, что для параметра **Расположение преобразования** задано значение **0, 0, 0** .</span><span class="sxs-lookup"><span data-stu-id="b5327-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="b5327-312">Установите для параметра **сбросить флаги** **сплошной цвет**.</span><span class="sxs-lookup"><span data-stu-id="b5327-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="b5327-313">Установить черный цвет **фона** для компонента камеры **, альфа 0 (шестнадцатеричный код: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="b5327-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![Настройка камеры](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="b5327-315">Глава 6 — Импорт библиотеки Newtonsoft</span><span class="sxs-lookup"><span data-stu-id="b5327-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="b5327-316">Чтобы упростить десериализацию и сериализацию объектов, полученных и отправленных службе Bot, необходимо загрузить библиотеку **Newtonsoft** .</span><span class="sxs-lookup"><span data-stu-id="b5327-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="b5327-317">[Совместимая версия уже организована с правильной структурой папок Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="b5327-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="b5327-318">Чтобы импортировать библиотеку Newtonsoft в проект, используйте пакет Unity, прилагаемый к этому курсу.</span><span class="sxs-lookup"><span data-stu-id="b5327-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="b5327-319">Добавьте *. пакет unitypackage* в Unity с помощью команды меню**настраиваемый пакет** **Импорт** >  **активов** > .</span><span class="sxs-lookup"><span data-stu-id="b5327-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Импорт библиотеки Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="b5327-321">В появившемся окне **Импорт пакета Unity** убедитесь, что выбраны все компоненты **подключаемых модулей** (включая).</span><span class="sxs-lookup"><span data-stu-id="b5327-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Импорт библиотеки Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="b5327-323">Нажмите кнопку **Импорт** , чтобы добавить элементы в проект.</span><span class="sxs-lookup"><span data-stu-id="b5327-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="b5327-324">Перейдите в папку **Newtonsoft** в разделе **подключаемые модули** в представлении проекта и выберите подключаемый модуль Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="b5327-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="b5327-325">Выбрав подключаемый модуль Newtonsoft, убедитесь, что не **установлен флажок**для **любой платформы** , а затем убедитесь, что **всаплайер** также не **установлен**, а затем нажмите кнопку **Применить**.</span><span class="sxs-lookup"><span data-stu-id="b5327-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="b5327-326">Это необходимо только для того, чтобы убедиться, что файлы настроены правильно.</span><span class="sxs-lookup"><span data-stu-id="b5327-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="b5327-327">Пометка этих подключаемых модулей настраивает их для использования только в редакторе Unity.</span><span class="sxs-lookup"><span data-stu-id="b5327-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="b5327-328">В папке WSA имеется другой набор, который будет использоваться после экспорта проекта из Unity.</span><span class="sxs-lookup"><span data-stu-id="b5327-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="b5327-329">Далее необходимо открыть папку **WSA** в папке **Newtonsoft**</span><span class="sxs-lookup"><span data-stu-id="b5327-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="b5327-330">Вы увидите копию того же файла, который вы только что настроили.</span><span class="sxs-lookup"><span data-stu-id="b5327-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="b5327-331">Выберите файл, а затем в инспекторе убедитесь, что</span><span class="sxs-lookup"><span data-stu-id="b5327-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="b5327-332">**Все платформы** не **отмечены**</span><span class="sxs-lookup"><span data-stu-id="b5327-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="b5327-333">**только** **Всаплайер** **установлен**</span><span class="sxs-lookup"><span data-stu-id="b5327-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="b5327-334">**Установлен** **процесс не**</span><span class="sxs-lookup"><span data-stu-id="b5327-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="b5327-335">Глава 7 — создание Боттаг</span><span class="sxs-lookup"><span data-stu-id="b5327-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="b5327-336">Создайте новый объект **Tag** с именем **боттаг**.</span><span class="sxs-lookup"><span data-stu-id="b5327-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="b5327-337">Выберите основную камеру в сцене.</span><span class="sxs-lookup"><span data-stu-id="b5327-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="b5327-338">Щелкните раскрывающееся меню тега на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="b5327-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="b5327-339">Щелкните **Добавить тег**.</span><span class="sxs-lookup"><span data-stu-id="b5327-339">Click on **Add Tag**.</span></span>

    ![Настройка камеры](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="b5327-341">**+** Щелкните символ.</span><span class="sxs-lookup"><span data-stu-id="b5327-341">Click on the **+** symbol.</span></span> <span data-ttu-id="b5327-342">Присвойте новому **тегу** имя **боттаг**, *Сохраните*.</span><span class="sxs-lookup"><span data-stu-id="b5327-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![Настройка камеры](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="b5327-344">**Не** применяйте **Боттаг** к основной камере.</span><span class="sxs-lookup"><span data-stu-id="b5327-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="b5327-345">Если вы случайно сделали это, обязательно замените основной тег камеры обратно на *маинкамера*.</span><span class="sxs-lookup"><span data-stu-id="b5327-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="b5327-346">Глава 8 — Создание класса Ботобжектс</span><span class="sxs-lookup"><span data-stu-id="b5327-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="b5327-347">Первым скриптом, который необходимо создать, является класс **ботобжектс** , который представляет собой пустой класс, так что ряд других объектов класса может храниться в пределах одного скрипта и обращаться к ним из других скриптов в сцене.</span><span class="sxs-lookup"><span data-stu-id="b5327-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="b5327-348">Создание этого класса является исключительно архитектурным выбором, поэтому эти объекты можно разместить в скрипте Bot, который будет создан далее в этом курсе.</span><span class="sxs-lookup"><span data-stu-id="b5327-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="b5327-349">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="b5327-349">To create this class:</span></span> 

1.  <span data-ttu-id="b5327-350">Щелкните правой кнопкой мыши на *панели проект*, а затем **Создайте > папку**.</span><span class="sxs-lookup"><span data-stu-id="b5327-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="b5327-351">Назовите папку **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="b5327-351">Name the folder **Scripts**.</span></span> 

    ![Создайте папку Scripts.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="b5327-353">Дважды щелкните папку Scripts  , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="b5327-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="b5327-354">Затем в этой папке щелкните правой кнопкой мыши и выберите **создать > C# скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b5327-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="b5327-355">Назовите сценарий **ботобжектс**.</span><span class="sxs-lookup"><span data-stu-id="b5327-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="b5327-356">Дважды щелкните новый скрипт **ботобжектс** , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b5327-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="b5327-357">Удалите содержимое скрипта и замените его следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="b5327-357">Delete the content of the script and replace it with the following code:</span></span>

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

6.  <span data-ttu-id="b5327-358">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5327-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="b5327-359">Глава 9 — Создание класса Газеинпут</span><span class="sxs-lookup"><span data-stu-id="b5327-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="b5327-360">Следующий класс, который предстоит создать, — это класс **газеинпут** .</span><span class="sxs-lookup"><span data-stu-id="b5327-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="b5327-361">Этот класс отвечает за:</span><span class="sxs-lookup"><span data-stu-id="b5327-361">This class is responsible for:</span></span>

- <span data-ttu-id="b5327-362">Создание курсора, который будет представлять *взгляд* на игрока.</span><span class="sxs-lookup"><span data-stu-id="b5327-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="b5327-363">Обнаружение объектов, которые попадают на взгляд игроку, и хранение ссылок на обнаруженные объекты.</span><span class="sxs-lookup"><span data-stu-id="b5327-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="b5327-364">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="b5327-364">To create this class:</span></span> 

1.  <span data-ttu-id="b5327-365">Перейдите к созданной ранее папке **Scripts** .</span><span class="sxs-lookup"><span data-stu-id="b5327-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="b5327-366">Щелкните правой кнопкой мыши внутри папки, **Создайте скрипт C# >** .</span><span class="sxs-lookup"><span data-stu-id="b5327-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="b5327-367">Вызовите скрипт **газеинпут**.</span><span class="sxs-lookup"><span data-stu-id="b5327-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="b5327-368">Дважды щелкните новый скрипт **газеинпут** , чтобы открыть его в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b5327-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="b5327-369">Вставьте следующую строку непосредственно в начале имени класса:</span><span class="sxs-lookup"><span data-stu-id="b5327-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="b5327-370">Затем добавьте следующие переменные в класс **газеинпут** над методом **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="b5327-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="b5327-371">Необходимо добавить код для метода **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="b5327-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="b5327-372">Он будет вызываться при инициализации класса:</span><span class="sxs-lookup"><span data-stu-id="b5327-372">This will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="b5327-373">Реализуйте метод, который будет создавать и настраивать курсор взгляда:</span><span class="sxs-lookup"><span data-stu-id="b5327-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

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

8.  <span data-ttu-id="b5327-374">Реализуйте методы, которые будут настраивать Райкаст из основной камеры и отслеживают текущий объект, на который осуществляется запись.</span><span class="sxs-lookup"><span data-stu-id="b5327-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
 
9.  <span data-ttu-id="b5327-375">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5327-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="b5327-376">Глава 10 — Создание класса Bot</span><span class="sxs-lookup"><span data-stu-id="b5327-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="b5327-377">Скрипт, который предстоит создать, называется **Bot**.</span><span class="sxs-lookup"><span data-stu-id="b5327-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="b5327-378">Это основной класс вашего приложения, который хранит:</span><span class="sxs-lookup"><span data-stu-id="b5327-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="b5327-379">Учетные данные для роботов веб-приложения</span><span class="sxs-lookup"><span data-stu-id="b5327-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="b5327-380">Метод, собирающий пользовательские команды</span><span class="sxs-lookup"><span data-stu-id="b5327-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="b5327-381">Метод, необходимый для инициации диалогов с помощью робота веб-приложения</span><span class="sxs-lookup"><span data-stu-id="b5327-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="b5327-382">Метод, необходимый для отправки сообщений в робот веб-приложения</span><span class="sxs-lookup"><span data-stu-id="b5327-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="b5327-383">Чтобы отправлять сообщения в службу Bot, соподпрограмма **сендмессажетобот ()** создает действие, которое представляет собой объект, распознаваемый программой Bot в качестве данных, отправленных пользователем.</span><span class="sxs-lookup"><span data-stu-id="b5327-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="b5327-384">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="b5327-384">To create this class:</span></span> 

1. <span data-ttu-id="b5327-385">Дважды щелкните папку Scripts  , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="b5327-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="b5327-386">Щелкните правой кнопкой мыши в  папке Scripts и выберите **создать C# > скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b5327-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="b5327-387">Присвойте сценарию имя **Bot**.</span><span class="sxs-lookup"><span data-stu-id="b5327-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="b5327-388">Дважды щелкните новый скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5327-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="b5327-389">Обновите пространства имен, как показано ниже, в верхней части класса **Bot** :</span><span class="sxs-lookup"><span data-stu-id="b5327-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="b5327-390">Внутри класса **Bot** добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="b5327-390">Inside the **Bot** class add the following variables:</span></span>

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
    > <span data-ttu-id="b5327-391">Обязательно вставьте **секретный ключ Bot** в переменную **ботсекрет** .</span><span class="sxs-lookup"><span data-stu-id="b5327-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="b5327-392">В начале этого курса вы заметили **секретный ключ** программы-робота, в  **[главе 2](#chapter-2---create-the-azure-bot-service), шаг 10**.</span><span class="sxs-lookup"><span data-stu-id="b5327-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="b5327-393">Необходимо добавить код для спящего режима **()** и **запуска ()** .</span><span class="sxs-lookup"><span data-stu-id="b5327-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

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

8. <span data-ttu-id="b5327-394">Добавьте два обработчика, которые вызываются библиотеками распознавания речи при начале и окончании захвата голоса.</span><span class="sxs-lookup"><span data-stu-id="b5327-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="b5327-395">*Диктатионрекогнизер* автоматически прекратит запись голоса пользователя, когда пользователь прекратит говорить.</span><span class="sxs-lookup"><span data-stu-id="b5327-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

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

1. <span data-ttu-id="b5327-396">Следующий обработчик собирает результат входного голоса пользователя и вызывает соподпрограмму, ответственную за отправку сообщения в службу веб-приложения Bot.</span><span class="sxs-lookup"><span data-stu-id="b5327-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

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

10. <span data-ttu-id="b5327-397">Для начала диалога с роботом вызывается следующая соподпрограмма.</span><span class="sxs-lookup"><span data-stu-id="b5327-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="b5327-398">Вы заметите, что после завершения вызова диалога он вызовет **сендмессажетокораутине ()** путем передачи ряда параметров, которые задают действие, которое будет отправлено в службу Bot, в виде пустого сообщения.</span><span class="sxs-lookup"><span data-stu-id="b5327-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="b5327-399">Это делается для запроса службы Bot на инициацию диалога.</span><span class="sxs-lookup"><span data-stu-id="b5327-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

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

11. <span data-ttu-id="b5327-400">Для создания действия, которое будет отправлено в службу Bot, вызывается следующая соподпрограмма.</span><span class="sxs-lookup"><span data-stu-id="b5327-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

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

12. <span data-ttu-id="b5327-401">Для запроса ответа после отправки действия в службу Bot вызывается следующая соподпрограмма.</span><span class="sxs-lookup"><span data-stu-id="b5327-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

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

13. <span data-ttu-id="b5327-402">Последний метод, который необходимо добавить в этот класс, необходим для вывода сообщения в сцене:</span><span class="sxs-lookup"><span data-stu-id="b5327-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

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
    > <span data-ttu-id="b5327-403">В консоли редактора Unity может появиться сообщение об ошибке, в котором отсутствует класс **сценеорганисер** .</span><span class="sxs-lookup"><span data-stu-id="b5327-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="b5327-404">Пропустите это сообщение, так как вы создадите этот класс позже в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="b5327-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="b5327-405">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5327-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="b5327-406">Глава 11 — Создание класса взаимодействий</span><span class="sxs-lookup"><span data-stu-id="b5327-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="b5327-407">Класс, который будет создан, теперь называется взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="b5327-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="b5327-408">Этот класс используется для обнаружения входных данных касания HoloLens от пользователя.</span><span class="sxs-lookup"><span data-stu-id="b5327-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="b5327-409">Если пользователь перейдет на объект *Bot* в сцене, и Bot готов к прослушиванию речевых входов, объект Bot изменит цвет на **красный** и начнет прослушивание входных данных голоса.</span><span class="sxs-lookup"><span data-stu-id="b5327-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="b5327-410">Этот класс наследует от класса **газеинпут** , поэтому он может ссылаться на метод **Start ()** и переменные из этого класса, обозначенные с помощью **base**.</span><span class="sxs-lookup"><span data-stu-id="b5327-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="b5327-411">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="b5327-411">To create this class:</span></span>

1.  <span data-ttu-id="b5327-412">Дважды щелкните папку Scripts  , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="b5327-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="b5327-413">Щелкните правой кнопкой мыши в  папке Scripts и выберите **создать C# > скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b5327-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="b5327-414">Назовите скрипт **взаимодействия**.</span><span class="sxs-lookup"><span data-stu-id="b5327-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="b5327-415">Дважды щелкните новый скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5327-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="b5327-416">Обновите пространства имен и наследование класса, как показано ниже, в верхней части класса **Interactions** :</span><span class="sxs-lookup"><span data-stu-id="b5327-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="b5327-417">Внутри класса **Interactions** добавьте следующую переменную:</span><span class="sxs-lookup"><span data-stu-id="b5327-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="b5327-418">Затем добавьте метод **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="b5327-418">Then add the **Start()** method:</span></span>

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

7.  <span data-ttu-id="b5327-419">Добавьте обработчик, который будет срабатывать, когда пользователь выполняет жест касания перед камерой HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5327-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

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

8. <span data-ttu-id="b5327-420">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5327-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="b5327-421">Глава 12 — создание класса Сценеорганисер</span><span class="sxs-lookup"><span data-stu-id="b5327-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="b5327-422">Последний класс, необходимый в этом лабораторном занятии, называется **сценеорганисер**.</span><span class="sxs-lookup"><span data-stu-id="b5327-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="b5327-423">Этот класс настраивает сцену программным способом, добавляя компоненты и скрипты в основную камеру и создавая соответствующие объекты в сцене.</span><span class="sxs-lookup"><span data-stu-id="b5327-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="b5327-424">Чтобы создать этот класс, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="b5327-424">To create this class:</span></span>

1.  <span data-ttu-id="b5327-425">Дважды щелкните папку Scripts  , чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="b5327-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="b5327-426">Щелкните правой кнопкой мыши в  папке Scripts и выберите **создать C# > скрипт**.</span><span class="sxs-lookup"><span data-stu-id="b5327-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="b5327-427">Назовите сценарий **сценеорганисер**.</span><span class="sxs-lookup"><span data-stu-id="b5327-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="b5327-428">Дважды щелкните новый скрипт, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5327-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="b5327-429">Внутри класса **сценеорганисер** добавьте следующие переменные:</span><span class="sxs-lookup"><span data-stu-id="b5327-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

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

6.  <span data-ttu-id="b5327-430">Затем добавьте методы **спящего режима ()** и **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="b5327-430">Then add the **Awake()** and **Start()** methods:</span></span>

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

7.  <span data-ttu-id="b5327-431">Добавьте следующий метод, отвечающий за создание объекта Bot в сцене и настройку параметров и компонентов:</span><span class="sxs-lookup"><span data-stu-id="b5327-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

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

7.  <span data-ttu-id="b5327-432">Добавьте следующий метод, отвечающий за создание объекта пользовательского интерфейса в сцене, представляющий ответы от программы-робота:</span><span class="sxs-lookup"><span data-stu-id="b5327-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

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

8.  <span data-ttu-id="b5327-433">Не забудьте сохранить изменения в *Visual Studio* перед возвратом в *Unity*.</span><span class="sxs-lookup"><span data-stu-id="b5327-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="b5327-434">В редакторе Unity перетащите сценарий **сценеорганисер** из папки Scripts на главную камеру.</span><span class="sxs-lookup"><span data-stu-id="b5327-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="b5327-435">Теперь компонент сцены Органисер должен отображаться на объекте основной камеры, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="b5327-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Создание службы Azure Bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="b5327-437">Глава 13 – перед сборкой</span><span class="sxs-lookup"><span data-stu-id="b5327-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="b5327-438">Чтобы выполнить тщательный тест приложения, необходимо загружать неопубликованные его на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5327-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="b5327-439">Перед этим убедитесь в том, что:</span><span class="sxs-lookup"><span data-stu-id="b5327-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="b5327-440">Все параметры, упомянутые в [**главе 4**](#Chapter-4-–-Set-up-the-unity-project) , заданы правильно.</span><span class="sxs-lookup"><span data-stu-id="b5327-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="b5327-441">**Сценеорганисер** скрипта прикреплен к главному объекту **Camera** .</span><span class="sxs-lookup"><span data-stu-id="b5327-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="b5327-442">В классе **Bot** убедитесь, что вы вставили секретный **ключ Bot** в переменную **ботсекрет** .</span><span class="sxs-lookup"><span data-stu-id="b5327-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="b5327-443">Глава 14 — сборка и загружать неопубликованные в HoloLens</span><span class="sxs-lookup"><span data-stu-id="b5327-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="b5327-444">Все необходимое для раздела Unity этого проекта теперь завершено, поэтому пришло время создать его из Unity.</span><span class="sxs-lookup"><span data-stu-id="b5327-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="b5327-445">Перейдите к разделу **параметры сборки**, **Файл > параметры сборки..** .</span><span class="sxs-lookup"><span data-stu-id="b5327-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="b5327-446">В окне " **параметры сборки** " щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="b5327-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Создание приложения из Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="b5327-448">Если это еще не так, то проекты Ticks **Unity C#** .</span><span class="sxs-lookup"><span data-stu-id="b5327-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="b5327-449">Щелкните **Сборка**.</span><span class="sxs-lookup"><span data-stu-id="b5327-449">Click **Build**.</span></span> <span data-ttu-id="b5327-450">Unity запустит окно **проводника** , в котором необходимо создать, а затем выбрать папку для сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="b5327-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b5327-451">Создайте эту папку сейчас и назовите ее **app**Name.</span><span class="sxs-lookup"><span data-stu-id="b5327-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="b5327-452">Затем выберите папку **приложения** и щелкните **выбрать папку**.</span><span class="sxs-lookup"><span data-stu-id="b5327-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="b5327-453">Unity начнет сборку проекта в папку **приложения** .</span><span class="sxs-lookup"><span data-stu-id="b5327-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="b5327-454">После того как Unity завершит сборку (может занять некоторое время), он откроет окно **проводника** в расположении сборки (проверьте панель задач, так как она может не всегда отображаться над окнами, но будет уведомлять о добавлении нового окна).</span><span class="sxs-lookup"><span data-stu-id="b5327-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="b5327-455">Глава 15 — развертывание в HoloLens</span><span class="sxs-lookup"><span data-stu-id="b5327-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="b5327-456">Для развертывания на HoloLens выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b5327-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="b5327-457">Вам потребуется IP-адрес HoloLens (для удаленного развертывания) и убедитесь, что HoloLens находится в **режиме разработчика**.</span><span class="sxs-lookup"><span data-stu-id="b5327-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="b5327-458">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="b5327-458">To do this:</span></span>

    1. <span data-ttu-id="b5327-459">Людьми HoloLens, откройте **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="b5327-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="b5327-460">Последовательно выберите пункты **сеть & интернет > Wi-Fi > дополнительные параметры**</span><span class="sxs-lookup"><span data-stu-id="b5327-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="b5327-461">Запишите **IPv4** -адрес.</span><span class="sxs-lookup"><span data-stu-id="b5327-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="b5327-462">Затем вернитесь к параметрам и **обновите & > безопасности для разработчиков** .</span><span class="sxs-lookup"><span data-stu-id="b5327-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="b5327-463">Задайте режим разработчика на.</span><span class="sxs-lookup"><span data-stu-id="b5327-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="b5327-464">Перейдите к новой сборке Unity (папка **приложения** ) и откройте файл решения в **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b5327-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="b5327-465">В **конфигурации решения** выберите **Отладка**.</span><span class="sxs-lookup"><span data-stu-id="b5327-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="b5327-466">На **платформе решения**выберите **x86**, **Удаленный компьютер**.</span><span class="sxs-lookup"><span data-stu-id="b5327-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Разверните решение из Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="b5327-468">Перейдите в **меню "сборка** " и щелкните " **Развернуть решение**", чтобы загружать неопубликованные приложение в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b5327-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="b5327-469">Теперь приложение должно отобразиться в списке установленных приложений в HoloLens, готовом к запуску.</span><span class="sxs-lookup"><span data-stu-id="b5327-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="b5327-470">Чтобы выполнить развертывание в иммерсивное виртуальную гарнитуру, задайте для **платформы решения** значение *локальный компьютер*и задайте для параметра **Конфигурация** значение *Отладка*( *x86* в качестве **платформы**).</span><span class="sxs-lookup"><span data-stu-id="b5327-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="b5327-471">Затем выполните развертывание на локальном компьютере с помощью **меню "сборка**" и выберите пункт " *Развернуть решение*".</span><span class="sxs-lookup"><span data-stu-id="b5327-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="b5327-472">Глава 16 — использование приложения в HoloLens</span><span class="sxs-lookup"><span data-stu-id="b5327-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="b5327-473">После запуска приложения вы увидите робота в качестве синей сферы перед вами.</span><span class="sxs-lookup"><span data-stu-id="b5327-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="b5327-474">Используйте **жест касания** , когда вы облакамие в сфере, чтобы начать беседу.</span><span class="sxs-lookup"><span data-stu-id="b5327-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="b5327-475">Ожидание запуска диалога (в пользовательском интерфейсе будет отображаться сообщение, когда оно произойдет).</span><span class="sxs-lookup"><span data-stu-id="b5327-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="b5327-476">Получив вводное сообщение от программы-робота, снова коснитесь программы-робота, чтобы он превратится в красный, и начнется прослушивание голоса.</span><span class="sxs-lookup"><span data-stu-id="b5327-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="b5327-477">После того как вы перестанете разговор, ваше приложение отправит сообщение в Bot, и Вы незамедлительно получите ответ, который будет отображаться в пользовательском интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="b5327-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="b5327-478">Повторите эту процедуру, чтобы отправить больше сообщений в программу-робот (нужно коснуться каждый раз, когда нужно нда сообщение).</span><span class="sxs-lookup"><span data-stu-id="b5327-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="b5327-479">В этом диалоговом окне показано, как Bot может хранить информацию (ваше имя), а также предоставлять известную информацию (например, товары, которые хранятся в запасах).</span><span class="sxs-lookup"><span data-stu-id="b5327-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="b5327-480">Вот некоторые вопросы, которые необходимо задать для программы-робота:</span><span class="sxs-lookup"><span data-stu-id="b5327-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="b5327-481">Готовое приложение Bot веб-приложения (v4)</span><span class="sxs-lookup"><span data-stu-id="b5327-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="b5327-482">Поздравляем! вы создали приложение смешанной реальности, которое использует робот веб-приложения Azure, Microsoft Bot Framework v4.</span><span class="sxs-lookup"><span data-stu-id="b5327-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Окончательный продукт](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b5327-484">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="b5327-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b5327-485">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="b5327-485">Exercise 1</span></span>

<span data-ttu-id="b5327-486">Структура диалога в этом лабораторном занятии является очень простой.</span><span class="sxs-lookup"><span data-stu-id="b5327-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="b5327-487">Используйте Microsoft LUIS, чтобы дать вашему естественному языку возможность понимания возможностей.</span><span class="sxs-lookup"><span data-stu-id="b5327-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b5327-488">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="b5327-488">Exercise 2</span></span>

<span data-ttu-id="b5327-489">Этот пример не включает в себя завершение диалога и перезапуск нового.</span><span class="sxs-lookup"><span data-stu-id="b5327-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="b5327-490">Чтобы сделать компонент Bot завершенным, попробуйте реализовать замыкание диалога.</span><span class="sxs-lookup"><span data-stu-id="b5327-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
