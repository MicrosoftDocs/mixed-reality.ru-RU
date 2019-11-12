---
title: MR и Azure 313 — служба центра Интернета вещей
description: Пройдите этот курс, чтобы узнать, как реализовать службу центра Интернета вещей Azure на виртуальной машине под управлением Ubuntu 16,4, а затем визуализировать данные сообщений с помощью Microsoft HoloLens или иммерсивного (VR) гарнитуры.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, ребро, центр Интернета вещей, учебник, API, уведомление, функции, таблицы, hololens, иммерсивное, VR, IOT, виртуальная машина, Ubuntu, Python
ms.openlocfilehash: bfb1518869892ed4899019d7b9c504a960e7db3f
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926833"
---
>[!NOTE]
><span data-ttu-id="aa581-104">Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="aa581-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="aa581-105">Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="aa581-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="aa581-106">Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="aa581-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="aa581-107">Они будут сохранены для продолжения работы на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="aa581-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="aa581-108">Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="aa581-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="aa581-109">Это уведомление будет обновлено ссылкой на эти учебники при их публикации.</span><span class="sxs-lookup"><span data-stu-id="aa581-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="aa581-110">MR и Azure 313: служба центра Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="aa581-110">MR and Azure 313: IoT Hub Service</span></span>

![результат курса](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="aa581-112">В этом курсе вы узнаете, как реализовать **службу центра Интернета вещей Azure** на виртуальной машине под управлением операционной системы Ubuntu 16,4.</span><span class="sxs-lookup"><span data-stu-id="aa581-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="aa581-113">Затем **приложение-функция Azure** будет использоваться для получения сообщений от виртуальной машины Ubuntu и сохранения результатов в **службе таблиц Azure**.</span><span class="sxs-lookup"><span data-stu-id="aa581-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="aa581-114">Затем вы сможете просматривать эти данные с помощью **Power BI** на гарнитуре Microsoft HoloLens или ИММЕРСИВНОЕ (VR).</span><span class="sxs-lookup"><span data-stu-id="aa581-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="aa581-115">Содержимое этого курса *применимо* к IOT Edgeным устройствам, но в рамках этого курса фокус будет находиться в среде виртуальной машины, поэтому доступ к физическому устройству пограничным устройства не требуется.</span><span class="sxs-lookup"><span data-stu-id="aa581-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="aa581-116">Прополнив этот курс, вы научитесь:</span><span class="sxs-lookup"><span data-stu-id="aa581-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="aa581-117">Разверните **модуль IOT Edge** на виртуальной машине (Ubuntu 16 OS), которая будет представлять ваше устройство Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="aa581-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="aa581-118">Добавьте **модель Tensorflow Azure пользовательское визуальное распознавание** в модуль ребра с кодом, который будет анализировать изображения, хранящиеся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="aa581-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="aa581-119">Настройте модуль для отправки сообщения результатов анализа обратно в **службу центра Интернета вещей**.</span><span class="sxs-lookup"><span data-stu-id="aa581-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="aa581-120">Используйте **приложение-функция Azure** для хранения сообщения в **таблице Azure**.</span><span class="sxs-lookup"><span data-stu-id="aa581-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="aa581-121">Настройте **Power BI** , чтобы получить сохраненное сообщение и создать отчет.</span><span class="sxs-lookup"><span data-stu-id="aa581-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="aa581-122">Визуализируйте данные сообщений IoT в **Power BI**.</span><span class="sxs-lookup"><span data-stu-id="aa581-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="aa581-123">К службам, которые вы будете использовать, относятся:</span><span class="sxs-lookup"><span data-stu-id="aa581-123">The Services you will use include:</span></span>

- <span data-ttu-id="aa581-124">**Центр Интернета вещей Azure** — это служба Microsoft Azure, которая позволяет разработчикам подключаться к ресурсам IOT, отслеживать их и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="aa581-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="aa581-125">Дополнительные сведения см. на странице [ **службы центра Интернета вещей Azure** ](https://azure.microsoft.com/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="aa581-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/services/iot-hub/).</span></span>

- <span data-ttu-id="aa581-126">**Реестр контейнеров Azure** — это служба Microsoft Azure, которая позволяет разработчикам хранить образы контейнеров для различных типов контейнеров.</span><span class="sxs-lookup"><span data-stu-id="aa581-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="aa581-127">Дополнительные сведения см. на странице [ **службы реестра контейнеров Azure** ](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="aa581-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/services/container-registry/).</span></span>

- <span data-ttu-id="aa581-128">**Azure приложение-функция** — это Microsoft Azure служба, которая позволяет разработчикам запускать в Azure небольшие фрагменты кода "функции".</span><span class="sxs-lookup"><span data-stu-id="aa581-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="aa581-129">Это позволяет делегировать работу в облако, а не локальное приложение, которое может иметь множество преимуществ.</span><span class="sxs-lookup"><span data-stu-id="aa581-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="aa581-130">**Функции Azure** поддерживают несколько языков разработки, включая C\#, F\#, Node. js, Java и PHP.</span><span class="sxs-lookup"><span data-stu-id="aa581-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="aa581-131">Дополнительные сведения см. на странице [ **функций Azure** ](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="aa581-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="aa581-132">**Хранилище Azure. таблицы** — это служба Microsoft Azure, которая позволяет разработчикам хранить структурированные, отличные от SQL данные в облаке, упрощая доступ к ним из любого места.</span><span class="sxs-lookup"><span data-stu-id="aa581-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="aa581-133">Служба может похвастаться проект без схемы, позволяя развитию таблиц по мере необходимости и, таким образом, очень гибкой.</span><span class="sxs-lookup"><span data-stu-id="aa581-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="aa581-134">Дополнительные сведения см. на странице [ **таблиц Azure** .](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="aa581-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="aa581-135">В этом курсе вы узнаете, как настроить и использовать службу центра Интернета вещей, а затем визуализировать ответ, предоставленный устройством.</span><span class="sxs-lookup"><span data-stu-id="aa581-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="aa581-136">Вы сможете применить эти концепции к настраиваемой программе установки службы центра Интернета вещей, которая может быть построена.</span><span class="sxs-lookup"><span data-stu-id="aa581-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="aa581-137">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="aa581-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="aa581-138">Хождение</span><span class="sxs-lookup"><span data-stu-id="aa581-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="aa581-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="aa581-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="aa581-140"><a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></span><span class="sxs-lookup"><span data-stu-id="aa581-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="aa581-141">MR и Azure 313: служба центра Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="aa581-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="aa581-142">✔️</span><span class="sxs-lookup"><span data-stu-id="aa581-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="aa581-143">✔️</span><span class="sxs-lookup"><span data-stu-id="aa581-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="aa581-144">Необходимые условия</span><span class="sxs-lookup"><span data-stu-id="aa581-144">Prerequisites</span></span>

<span data-ttu-id="aa581-145">Наиболее актуальные предварительные требования для разработки с использованием смешанной реальности, включая Microsoft HoloLens, см. в статье [Установка средств](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) .</span><span class="sxs-lookup"><span data-stu-id="aa581-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="aa581-146">Этот учебник предназначен для разработчиков, имеющих базовый опыт работы с Python.</span><span class="sxs-lookup"><span data-stu-id="aa581-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="aa581-147">Также имейте в виду, что предварительные требования и письменные инструкции в этом документе отражают, что проверялось и проверено на момент написания статьи (Июль 2018).</span><span class="sxs-lookup"><span data-stu-id="aa581-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="aa581-148">Вы можете использовать новейшее программное обеспечение, как указано в статье [Установка средств](install-the-tools.md) , но не следует предполагать, что информация в этом курсе будет полностью соответствовать тому, что вы найдете в более новом программном обеспечении, чем указано ниже.</span><span class="sxs-lookup"><span data-stu-id="aa581-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="aa581-149">Требуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="aa581-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="aa581-150">Windows 10 для дизайнеров с обновлением (или более поздней версии), **режим разработчика включен**</span><span class="sxs-lookup"><span data-stu-id="aa581-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="aa581-151">Невозможно запустить виртуальную машину с помощью Hyper-V в Windows 10 Домашняя.</span><span class="sxs-lookup"><span data-stu-id="aa581-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="aa581-152">Пакет SDK для Windows 10 (последняя версия)</span><span class="sxs-lookup"><span data-stu-id="aa581-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="aa581-153">В HoloLens **включен режим разработчика**</span><span class="sxs-lookup"><span data-stu-id="aa581-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="aa581-154">Visual Studio 2017.15.4 (используется только для доступа к Cloud Explorer Azure)</span><span class="sxs-lookup"><span data-stu-id="aa581-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="aa581-155">Доступ к Интернету для Azure и для службы центра Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="aa581-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="aa581-156">Для получения дополнительных сведений перейдите [по ссылке на страницу службы центра Интернета вещей](https://azure.microsoft.com/services/iot-hub/) .</span><span class="sxs-lookup"><span data-stu-id="aa581-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/services/iot-hub/)</span></span>
- <span data-ttu-id="aa581-157">Модель машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="aa581-157">A machine learning model.</span></span> <span data-ttu-id="aa581-158">Если вы не готовы использовать модель, [вы можете использовать модель, предоставленную в этом курсе](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="aa581-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="aa581-159">Программное обеспечение **Hyper-V** , включенное на компьютере разработки Windows 10.</span><span class="sxs-lookup"><span data-stu-id="aa581-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="aa581-160">Виртуальная машина под управлением Ubuntu (16,4 или 18,4), выполняемая на компьютере разработки, или можно использовать отдельный компьютер под управлением Linux (Ubuntu 16,4 или 18,4).</span><span class="sxs-lookup"><span data-stu-id="aa581-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="aa581-161">Дополнительные сведения о создании виртуальной машины в Windows с помощью Hyper-V см. в [разделе «перед](#before-you-start)началом работы». (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="aa581-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="aa581-162">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="aa581-162">Before you start</span></span>

1. <span data-ttu-id="aa581-163">Настройка и тестирование HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aa581-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="aa581-164">Если вам нужна поддержка по настройке HoloLens, [обязательно посетите статью Настройка hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="aa581-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="aa581-165">Рекомендуется выполнять настройку **калибровки** и **датчика** при разработке нового приложения HoloLens (иногда это может помочь в выполнении этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="aa581-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="aa581-166">Чтобы получить справку по калибровке, перейдите по этой [ссылке в статью калибровка HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="aa581-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="aa581-167">Чтобы получить справку по настройке датчика, перейдите [по ссылке в статью Настройка датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="aa581-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="aa581-168">Настройте **виртуальную машину Ubuntu** с помощью **Hyper-V**.</span><span class="sxs-lookup"><span data-stu-id="aa581-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="aa581-169">Следующие ресурсы помогут вам в процессе.</span><span class="sxs-lookup"><span data-stu-id="aa581-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="aa581-170">Сначала перейдите по этой ссылке, чтобы [скачать ISO-образ Ubuntu 16.04.4 LTS (Xenial Xerus)](https://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="aa581-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](https://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="aa581-171">Выберите **образ настольного компьютера 64-разрядный компьютер (AMD64)** .</span><span class="sxs-lookup"><span data-stu-id="aa581-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="aa581-172">Убедитесь, что на компьютере с Windows 10 включен **Hyper-V** .</span><span class="sxs-lookup"><span data-stu-id="aa581-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="aa581-173">Вы можете перейти по этой ссылке, чтобы получить рекомендации по [установке и включению Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="aa581-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="aa581-174">Запустите Hyper-V и создайте новую виртуальную машину Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="aa581-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="aa581-175">Вы можете перейти по этой ссылке, чтобы получить пошаговое [руководство по созданию виртуальной машины с помощью Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="aa581-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="aa581-176">При запросе на **установку операционной системы из файла загрузочного образа**выберите ранее ЗАГРУЖЕНный ISO-образ **Ubuntu** .</span><span class="sxs-lookup"><span data-stu-id="aa581-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aa581-177">Использование **быстрого создания Hyper-V** не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="aa581-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="aa581-178">Глава 1. Получение модели Пользовательское визуальное распознавание</span><span class="sxs-lookup"><span data-stu-id="aa581-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="aa581-179">С этим курсом у вас будет доступ к [предварительно созданной модели пользовательское визуальное распознавание](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) , которая обнаруживает клавиатуры и мыши на изображениях.</span><span class="sxs-lookup"><span data-stu-id="aa581-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="aa581-180">Если вы используете это, перейдите к [главе 2](#chapter-2---the-container-registry-service).</span><span class="sxs-lookup"><span data-stu-id="aa581-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="aa581-181">Однако можно выполнить следующие действия, если вы хотите использовать собственную модель Пользовательское визуальное распознавание:</span><span class="sxs-lookup"><span data-stu-id="aa581-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="aa581-182">В **проекте пользовательское визуальное распознавание** перейдите на вкладку **Performance (производительность** ).</span><span class="sxs-lookup"><span data-stu-id="aa581-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="aa581-183">Для экспорта модели модель должна использовать *компактный* домен.</span><span class="sxs-lookup"><span data-stu-id="aa581-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="aa581-184">Вы можете изменить домен моделей в параметрах проекта.</span><span class="sxs-lookup"><span data-stu-id="aa581-184">You can change your models domain in the settings for your project.</span></span>

    ![Вкладка "производительность"](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="aa581-186">Выберите **итерацию** , которую необходимо экспортировать, и щелкните **Export (экспорт**).</span><span class="sxs-lookup"><span data-stu-id="aa581-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="aa581-187">Появится колонка.</span><span class="sxs-lookup"><span data-stu-id="aa581-187">A blade will appear.</span></span>

    ![Колонка экспорта](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="aa581-189">В колонке щелкните **файл DOCKER**.</span><span class="sxs-lookup"><span data-stu-id="aa581-189">In the blade click **Docker File**.</span></span>

    ![Выбор DOCKER](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="aa581-191">Щелкните **Linux** в раскрывающемся меню и выберите **скачать**.</span><span class="sxs-lookup"><span data-stu-id="aa581-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Нажмите кнопку Скачать.](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="aa581-193">Распакуйте содержимое.</span><span class="sxs-lookup"><span data-stu-id="aa581-193">Unzip the content.</span></span> <span data-ttu-id="aa581-194">Он будет использоваться позже в этом курсе.</span><span class="sxs-lookup"><span data-stu-id="aa581-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="aa581-195">Глава 2. Служба реестра контейнеров</span><span class="sxs-lookup"><span data-stu-id="aa581-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="aa581-196">**Служба реестра контейнеров** — это репозиторий, который используется для размещения контейнеров.</span><span class="sxs-lookup"><span data-stu-id="aa581-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="aa581-197">**Служба центра Интернета вещей** , которая будет построена и использована в этом курсе, ссылается на **службу реестра контейнеров** , чтобы получить контейнеры для развертывания на пограничном устройстве.</span><span class="sxs-lookup"><span data-stu-id="aa581-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="aa581-198">Сначала перейдите по [ссылке на портал Azure](https://portal.azure.com/)и войдите в систему с вашими учетными данными.</span><span class="sxs-lookup"><span data-stu-id="aa581-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="aa581-199">Перейдите к разделу **Создание ресурса** и найдите **Реестр контейнеров**.</span><span class="sxs-lookup"><span data-stu-id="aa581-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![реестр контейнеров](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="aa581-201">Щелкните **создать**.</span><span class="sxs-lookup"><span data-stu-id="aa581-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="aa581-202">Задайте параметры установки службы:</span><span class="sxs-lookup"><span data-stu-id="aa581-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="aa581-203">Вставьте имя проекта, в этом примере — **иоткрегистри**.</span><span class="sxs-lookup"><span data-stu-id="aa581-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="aa581-204">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="aa581-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="aa581-205">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки и управления выставлением счетов за сбор ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="aa581-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="aa581-206">Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aa581-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="aa581-207">Задайте расположение службы.</span><span class="sxs-lookup"><span data-stu-id="aa581-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="aa581-208">Установите для параметра **пользователь с правами администратора** значение **включено**.</span><span class="sxs-lookup"><span data-stu-id="aa581-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="aa581-209">Задайте для параметра **номер SKU** значение **базовый**.</span><span class="sxs-lookup"><span data-stu-id="aa581-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="aa581-210">Щелкните **создать** и дождитесь создания служб.</span><span class="sxs-lookup"><span data-stu-id="aa581-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="aa581-211">Когда появится уведомление об успешном создании *реестра контейнеров*, щелкните **Перейти к ресурсу** , который будет перенаправлен на страницу службы.</span><span class="sxs-lookup"><span data-stu-id="aa581-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="aa581-212">На странице Служба *реестра контейнеров* щелкните **ключи доступа**.</span><span class="sxs-lookup"><span data-stu-id="aa581-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="aa581-213">Запишите (вы можете использовать Блокнот) со следующими параметрами:</span><span class="sxs-lookup"><span data-stu-id="aa581-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="aa581-214">**Сервер входа**</span><span class="sxs-lookup"><span data-stu-id="aa581-214">**Login Server**</span></span>
    2. <span data-ttu-id="aa581-215">**Имен**</span><span class="sxs-lookup"><span data-stu-id="aa581-215">**Username**</span></span>
    3. <span data-ttu-id="aa581-216">**Пароль**</span><span class="sxs-lookup"><span data-stu-id="aa581-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="aa581-217">Глава 3. Служба центра Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="aa581-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="aa581-218">Теперь вы начнете создавать и настраивать **службу центра Интернета вещей**.</span><span class="sxs-lookup"><span data-stu-id="aa581-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="aa581-219">Если вы еще не вошли в систему, войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="aa581-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="aa581-220">После входа в систему щелкните **создать ресурс** в верхнем левом углу и найдите **центр Интернета вещей**и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="aa581-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![Поиск учетной записи хранения](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="aa581-222">На новой странице будет представлено описание службы **учетной записи хранения** .</span><span class="sxs-lookup"><span data-stu-id="aa581-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="aa581-223">В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="aa581-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="aa581-225">После нажатия кнопки **создать**появится панель:</span><span class="sxs-lookup"><span data-stu-id="aa581-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="aa581-226">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="aa581-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="aa581-227">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки счетов и управления ими для коллекции ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="aa581-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="aa581-228">Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aa581-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="aa581-229">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="aa581-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="aa581-230">Выберите нужное **Расположение** (Используйте то же расположение для всех служб, создаваемых в этом курсе).</span><span class="sxs-lookup"><span data-stu-id="aa581-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="aa581-231">Вставьте нужное **имя** для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="aa581-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="aa581-232">В нижней части страницы щелкните **Далее: размер и масштаб**.</span><span class="sxs-lookup"><span data-stu-id="aa581-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="aa581-234">На этой странице выберите **ценовую категорию и уровень масштабирования** (если это ваш первый экземпляр службы центра Интернета вещей, для вас должен быть доступен бесплатный уровень).</span><span class="sxs-lookup"><span data-stu-id="aa581-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="aa581-235">Щелкните **Проверка и создать**.</span><span class="sxs-lookup"><span data-stu-id="aa581-235">Click on **Review + Create**.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="aa581-237">Проверьте параметры и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="aa581-237">Review your settings and click on **Create**.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="aa581-239">После того как уведомление появится, уведомляя об успешном создании службы *центра Интернета вещей* , щелкните **Перейти к ресурсу** , который будет перенаправлен на страницу службы.</span><span class="sxs-lookup"><span data-stu-id="aa581-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="aa581-241">Прокрутите боковую панель слева, пока вы не увидите *Автоматическое управление устройствами*, щелкните **IOT Edge**.</span><span class="sxs-lookup"><span data-stu-id="aa581-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="aa581-243">В появившемся окне щелкните **Add IOT Edge Device (добавить устройство**).</span><span class="sxs-lookup"><span data-stu-id="aa581-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="aa581-244">Справа появится колонка.</span><span class="sxs-lookup"><span data-stu-id="aa581-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="aa581-245">В колонке укажите для нового устройства **идентификатор устройства** (имя по своему усмотрению).</span><span class="sxs-lookup"><span data-stu-id="aa581-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="aa581-246">Затем нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="aa581-246">Then, click **Save**.</span></span> <span data-ttu-id="aa581-247">*Первичный* и *вторичный ключи* будут автоматически формироваться, если **Автоматическое создание** тактов было создано автоматически.</span><span class="sxs-lookup"><span data-stu-id="aa581-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="aa581-249">Вы вернетесь к разделу *устройства IOT Edge* , где будет указано новое устройство.</span><span class="sxs-lookup"><span data-stu-id="aa581-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="aa581-250">Щелкните новое устройство (выделено красным цветом на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="aa581-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="aa581-252">На появившейся странице *сведений об устройстве* сделайте копию **строки подключения** (первичный ключ).</span><span class="sxs-lookup"><span data-stu-id="aa581-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="aa581-254">Вернитесь на панель слева и щелкните *политики общего доступа*, чтобы открыть ее.</span><span class="sxs-lookup"><span data-stu-id="aa581-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="aa581-255">На появившейся странице щелкните **iothubowner**, и в правой части экрана появится колонка.</span><span class="sxs-lookup"><span data-stu-id="aa581-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="aa581-256">Запишите (в Блокноте) **строку подключения** (первичный ключ) для последующего использования при настройке *строки подключения* для устройства.</span><span class="sxs-lookup"><span data-stu-id="aa581-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="aa581-258">Глава 4. Настройка среды разработки</span><span class="sxs-lookup"><span data-stu-id="aa581-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="aa581-259">Чтобы создать и развернуть модули для *центра Интернета вещей*, вам потребуется установить следующие компоненты на компьютере разработки под Windows 10:</span><span class="sxs-lookup"><span data-stu-id="aa581-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="aa581-260">[DOCKER для Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), будет предложено создать учетную запись для загрузки.</span><span class="sxs-lookup"><span data-stu-id="aa581-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="aa581-261">[![скачать DOCKER для Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="aa581-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="aa581-262">Для запуска DOCKER требуется *Windows 10 Pro*, *Enterprise 14393*или *Windows Server 2016 RTM*.</span><span class="sxs-lookup"><span data-stu-id="aa581-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="aa581-263">Если вы используете другие версии Windows 10, можно попробовать установить DOCKER с помощью [панели элементов DOCKER](https://docs.docker.com/toolbox/toolbox_install_windows/).</span><span class="sxs-lookup"><span data-stu-id="aa581-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="aa581-264">[Python 3,6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="aa581-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="aa581-265">[![скачать Python 3,6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="aa581-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="aa581-266">[Visual Studio Code (также называется VS Code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="aa581-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="aa581-267">[![загрузки VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="aa581-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="aa581-268">После установки программного обеспечения, упомянутого выше, необходимо перезагрузить компьютер.</span><span class="sxs-lookup"><span data-stu-id="aa581-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="aa581-269">Глава 5. Настройка среды Ubuntu</span><span class="sxs-lookup"><span data-stu-id="aa581-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="aa581-270">Теперь можно перейти к настройке устройства **под управлением ОС Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="aa581-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="aa581-271">Выполните следующие действия, чтобы установить необходимое программное обеспечение для развертывания контейнеров на доске:</span><span class="sxs-lookup"><span data-stu-id="aa581-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa581-272">Перед выполнением команд терминала с помощью команды **sudo** необходимо выполнить от имени администратора.</span><span class="sxs-lookup"><span data-stu-id="aa581-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="aa581-273">такого</span><span class="sxs-lookup"><span data-stu-id="aa581-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="aa581-274">Откройте **терминал Ubuntu**и используйте следующую команду для установки **PIP**:</span><span class="sxs-lookup"><span data-stu-id="aa581-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! Подсказка]<span data-ttu-id="aa581-275"> можно легко открыть *терминал* с помощью сочетания клавиш: **CTRL + ALT + T**.</span><span class="sxs-lookup"><span data-stu-id="aa581-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="aa581-276">В этой главе вам может быть предложено, по *терминалу*, получить разрешение на использование хранилища устройства и ввести **y/n** (да или нет), ввести **"y"** , а затем нажать клавишу **Ввод** , чтобы принять.</span><span class="sxs-lookup"><span data-stu-id="aa581-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="aa581-277">После завершения этой команды используйте следующую команду, чтобы установить **фигурную скобку**:</span><span class="sxs-lookup"><span data-stu-id="aa581-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="aa581-278">После установки **PIP** и **фигур** используйте следующую команду для установки **среды выполнения IOT Edge**. это необходимо для развертывания модулей на доске и управления этими модулями:</span><span class="sxs-lookup"><span data-stu-id="aa581-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="aa581-279">На этом этапе вам будет предложено открыть *файл конфигурации среды выполнения*, чтобы вставить **строку подключения устройства**, которая была записана (в Блокноте) при создании **службы центра Интернета вещей** (в[шаге 14 раздела 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="aa581-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="aa581-280">Чтобы открыть этот файл, выполните в терминале следующую строку:</span><span class="sxs-lookup"><span data-stu-id="aa581-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="aa581-281">Появится файл **config. YAML** , который будет готов к редактированию:</span><span class="sxs-lookup"><span data-stu-id="aa581-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="aa581-282">При открытии этот файл может быть несколько запутанным.</span><span class="sxs-lookup"><span data-stu-id="aa581-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="aa581-283">Будет изменен текст этого файла в самом *терминале* .</span><span class="sxs-lookup"><span data-stu-id="aa581-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="aa581-284">Используйте клавиши со стрелками на клавиатуре для прокрутки вниз (необходимо прокрутить немного вниз), чтобы перейти к строке, содержащей ":</span><span class="sxs-lookup"><span data-stu-id="aa581-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="aa581-285">" **\<добавить строку подключения устройства >** ".</span><span class="sxs-lookup"><span data-stu-id="aa581-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="aa581-286">Замените строку, **включая квадратные скобки**, **строкой подключения устройства** , отмеченной ранее.</span><span class="sxs-lookup"><span data-stu-id="aa581-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="aa581-287">После ввода строки подключения нажмите клавиши **CTRL + X** , чтобы сохранить файл.</span><span class="sxs-lookup"><span data-stu-id="aa581-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="aa581-288">Появится запрос на подтверждение, введя **Y**. Затем нажмите клавишу **Ввод** , чтобы подтвердить.</span><span class="sxs-lookup"><span data-stu-id="aa581-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="aa581-289">Вернемся к обычному *терминалу*.</span><span class="sxs-lookup"><span data-stu-id="aa581-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="aa581-290">После успешного выполнения этих команд будет установлена **Среда выполнения IOT Edge**.</span><span class="sxs-lookup"><span data-stu-id="aa581-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="aa581-291">После инициализации среда выполнения будет запускаться отдельно при каждом включении устройства и будет находиться в фоновом режиме, ожидая развертывания модулей из **службы центра Интернета вещей**.</span><span class="sxs-lookup"><span data-stu-id="aa581-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="aa581-292">Выполните следующую командную строку, чтобы инициализировать *среду выполнения IOT Edge*:</span><span class="sxs-lookup"><span data-stu-id="aa581-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="aa581-293">Если вы внесете изменения в файл. YAML или указанную выше настройку, вам потребуется снова выполнить указанную выше строку перезагрузки в окне *терминала*.</span><span class="sxs-lookup"><span data-stu-id="aa581-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="aa581-294">Проверьте состояние *среды выполнения IOT Edge* , выполнив следующую командную строку.</span><span class="sxs-lookup"><span data-stu-id="aa581-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="aa581-295">Среда выполнения должна отображаться с состоянием **активно (работает)** в зеленом тексте.</span><span class="sxs-lookup"><span data-stu-id="aa581-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="aa581-296">Нажмите клавиши **CTRL + C** , чтобы закрыть страницу состояние.</span><span class="sxs-lookup"><span data-stu-id="aa581-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="aa581-297">Чтобы убедиться, что *Среда выполнения IOT Edge* правильно извлекать контейнеры, введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="aa581-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="aa581-298">Появится список с двумя (2) контейнерами.</span><span class="sxs-lookup"><span data-stu-id="aa581-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="aa581-299">Это модули по умолчанию, которые автоматически создаются службой центра Интернета вещей (edgeAgent и edgeHub).</span><span class="sxs-lookup"><span data-stu-id="aa581-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="aa581-300">После создания и развертывания собственных модулей они будут отображаться в этом списке под заданными по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aa581-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="aa581-301">Глава 6. Установка расширений</span><span class="sxs-lookup"><span data-stu-id="aa581-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa581-302">Следующие несколько глав (6-9) будут выполняться на компьютере с Windows 10.</span><span class="sxs-lookup"><span data-stu-id="aa581-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="aa581-303">Откройте **VS Code**.</span><span class="sxs-lookup"><span data-stu-id="aa581-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="aa581-304">Нажмите кнопку **расширения** (квадрат) на левой панели VS Code, чтобы открыть **Панель расширения**.</span><span class="sxs-lookup"><span data-stu-id="aa581-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="aa581-305">Найдите и установите следующие расширения (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="aa581-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="aa581-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="aa581-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="aa581-307">Набор средств Azure IoT Toolkit</span><span class="sxs-lookup"><span data-stu-id="aa581-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="aa581-308">Docker</span><span class="sxs-lookup"><span data-stu-id="aa581-308">Docker</span></span>   

    ![Создание контейнера](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="aa581-310">После установки расширений закройте и снова откройте VS Code.</span><span class="sxs-lookup"><span data-stu-id="aa581-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="aa581-311">Если VS Code открыть еще раз, перейдите к **просмотру** > **интегрированный терминал**.</span><span class="sxs-lookup"><span data-stu-id="aa581-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="aa581-312">Теперь будет установлен **Cookiecutter**.</span><span class="sxs-lookup"><span data-stu-id="aa581-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="aa581-313">В окне терминала выполните следующую команду Bash:</span><span class="sxs-lookup"><span data-stu-id="aa581-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Указание]<span data-ttu-id="aa581-314"> Если у вас возникли проблемы с этой командой:</span><span class="sxs-lookup"><span data-stu-id="aa581-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="aa581-315">Перезапустите VS Code и (или) компьютер.</span><span class="sxs-lookup"><span data-stu-id="aa581-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="aa581-316">Может потребоваться переключить **терминал VS Code** на тот, который использовался для установки Python, например **PowerShell** (особенно если среда Python уже установлена на компьютере).</span><span class="sxs-lookup"><span data-stu-id="aa581-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="aa581-317">Открыв окно терминала, вы увидите раскрывающееся меню в правой части окна терминала.</span><span class="sxs-lookup"><span data-stu-id="aa581-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="aa581-318">![создать контейнер](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="aa581-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="aa581-319">Убедитесь, что путь установки **Python** добавлен в качестве **переменной среды** на компьютере.</span><span class="sxs-lookup"><span data-stu-id="aa581-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="aa581-320">Cookiecutter должен быть частью того же пути расположения.</span><span class="sxs-lookup"><span data-stu-id="aa581-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="aa581-321">Чтобы получить [Дополнительные сведения о переменных среды](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), перейдите по этой ссылке.</span><span class="sxs-lookup"><span data-stu-id="aa581-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="aa581-322">После завершения установки **Cookiecutter** необходимо перезапустить компьютер, чтобы **Cookiecutter** был распознан как команда в среде системы.</span><span class="sxs-lookup"><span data-stu-id="aa581-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="aa581-323">Глава 7. Создание решения-контейнера</span><span class="sxs-lookup"><span data-stu-id="aa581-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="aa581-324">На этом этапе необходимо создать контейнер с модулем, который будет помещен в *Реестр контейнеров*.</span><span class="sxs-lookup"><span data-stu-id="aa581-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="aa581-325">После отправки контейнера вы будете использовать службу *ребра центра Интернета вещей* , чтобы развернуть ее на устройстве, где выполняется *IOT Edge среды выполнения*.</span><span class="sxs-lookup"><span data-stu-id="aa581-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="aa581-326">В VS Code выберите **вид** > **Палитра команд**.</span><span class="sxs-lookup"><span data-stu-id="aa581-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="aa581-327">В палитре найдите и запустите **Azure IOT Edge: новое решение IOT ребро**.</span><span class="sxs-lookup"><span data-stu-id="aa581-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="aa581-328">Перейдите в расположение, в котором нужно создать решение.</span><span class="sxs-lookup"><span data-stu-id="aa581-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="aa581-329">Нажмите клавишу **Ввод** , чтобы принять расположение.</span><span class="sxs-lookup"><span data-stu-id="aa581-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="aa581-330">Укажите имя для решения.</span><span class="sxs-lookup"><span data-stu-id="aa581-330">Give a name to your solution.</span></span> <span data-ttu-id="aa581-331">Нажмите клавишу **Ввод** , чтобы подтвердить указанное имя.</span><span class="sxs-lookup"><span data-stu-id="aa581-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="aa581-332">Теперь вам будет предложено выбрать платформу шаблонов для решения.</span><span class="sxs-lookup"><span data-stu-id="aa581-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="aa581-333">Щелкните **модуль Python**.</span><span class="sxs-lookup"><span data-stu-id="aa581-333">Click **Python Module**.</span></span> <span data-ttu-id="aa581-334">Нажмите клавишу **Ввод** , чтобы подтвердить этот вариант.</span><span class="sxs-lookup"><span data-stu-id="aa581-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="aa581-335">Присвойте имя модулю.</span><span class="sxs-lookup"><span data-stu-id="aa581-335">Give a name to your module.</span></span> <span data-ttu-id="aa581-336">Нажмите клавишу **Ввод** , чтобы подтвердить имя модуля.</span><span class="sxs-lookup"><span data-stu-id="aa581-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="aa581-337">Обязательно запишите имя модуля (в Блокноте), так как оно будет использовано позже.</span><span class="sxs-lookup"><span data-stu-id="aa581-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="aa581-338">На палитре появится предварительно созданный адрес *репозитория образов DOCKER* .</span><span class="sxs-lookup"><span data-stu-id="aa581-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="aa581-339">Он будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aa581-339">It will look like:</span></span>

    <span data-ttu-id="aa581-340">**localhost: 5000/— имя модуля**.</span><span class="sxs-lookup"><span data-stu-id="aa581-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="aa581-341">Удалите **localhost: 5000.** на его месте вставьте адрес **сервера входа** в *Реестр контейнеров* , который вы заметили при создании **службы реестра контейнеров** ([на шаге 8 главы 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="aa581-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="aa581-342">Нажмите клавишу **Ввод** , чтобы подтвердить адрес.</span><span class="sxs-lookup"><span data-stu-id="aa581-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="aa581-343">На этом этапе будет создан решение, содержащее шаблон для модуля Python, и его структура будет отображаться на **вкладке "Обзор"** в области VS Code в левой части экрана.</span><span class="sxs-lookup"><span data-stu-id="aa581-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="aa581-344">Если **вкладка "Обзор"** не открыта, ее можно открыть, нажав кнопку "сверху" на панели слева.</span><span class="sxs-lookup"><span data-stu-id="aa581-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Создание контейнера](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="aa581-346">Последний шаг в этой главе — щелкнуть и открыть **env-файл**на **вкладке "Обзор"** и добавить **имя пользователя** и **пароль** *реестра контейнеров* .</span><span class="sxs-lookup"><span data-stu-id="aa581-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="aa581-347">Этот файл игнорируется Git, но при построении контейнера задаются учетные данные для доступа к **службе реестра контейнеров**.</span><span class="sxs-lookup"><span data-stu-id="aa581-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Создание контейнера](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="aa581-349">Глава 8. изменение решения контейнера</span><span class="sxs-lookup"><span data-stu-id="aa581-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="aa581-350">Теперь вы сможете завершить решение контейнера, обновив следующие файлы:</span><span class="sxs-lookup"><span data-stu-id="aa581-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="aa581-351">*скрипт<span></span>Main. корректировки* Python.</span><span class="sxs-lookup"><span data-stu-id="aa581-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="aa581-352">*требования. txt*.</span><span class="sxs-lookup"><span data-stu-id="aa581-352">*requirements.txt*.</span></span>
- <span data-ttu-id="aa581-353">*развертывание. Template. JSON*.</span><span class="sxs-lookup"><span data-stu-id="aa581-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="aa581-354">*Dockerfile. AMD64*</span><span class="sxs-lookup"><span data-stu-id="aa581-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="aa581-355">Затем вы создадите папку *Images* , используемую сценарием Python, чтобы проверить, соответствуют ли образы *модели пользовательское визуальное распознавание*.</span><span class="sxs-lookup"><span data-stu-id="aa581-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="aa581-356">Наконец, вы добавите файл *labels. txt* , чтобы облегчить чтение модели, и файл *model. Pb* , который является моделью.</span><span class="sxs-lookup"><span data-stu-id="aa581-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="aa581-357">После открытия VS Code перейдите в папку модуля и найдите сценарий с именем **Main<span></span>. Корректировка**.</span><span class="sxs-lookup"><span data-stu-id="aa581-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="aa581-358">Дважды щелкните, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="aa581-358">Double-click to open it.</span></span>

2. <span data-ttu-id="aa581-359">Удалите содержимое файла и вставьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="aa581-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="aa581-360">Откройте файл с именем **требований. txt**и замените его содержимое следующим:</span><span class="sxs-lookup"><span data-stu-id="aa581-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="aa581-361">Откройте файл **Deployment. Template. JSON**и замените его содержимое следующим правилом:</span><span class="sxs-lookup"><span data-stu-id="aa581-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="aa581-362">Так как вы будете иметь собственную уникальную структуру JSON, вам потребуется изменить ее вручную (вместо копирования примера).</span><span class="sxs-lookup"><span data-stu-id="aa581-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="aa581-363">Чтобы сделать это простым, используйте приведенное ниже изображение в качестве инструкции.</span><span class="sxs-lookup"><span data-stu-id="aa581-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="aa581-364">Области, которые будут выглядеть иначе, но которые **не следует изменять, выделяются желтым**цветом.</span><span class="sxs-lookup"><span data-stu-id="aa581-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="aa581-365">**Разделы, которые необходимо удалить, отмечены красным цветом.**</span><span class="sxs-lookup"><span data-stu-id="aa581-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="aa581-366">Будьте внимательны, чтобы удалить нужные квадратные скобки, а также удалить запятые.</span><span class="sxs-lookup"><span data-stu-id="aa581-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Создание контейнера](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="aa581-368">Заполненный JSON должен выглядеть, как на следующем рисунке (Однако, с уникальными отличиями: *имя пользователя, пароль или модуль/ссылки на модуль*):</span><span class="sxs-lookup"><span data-stu-id="aa581-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Создание контейнера](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="aa581-370">Откройте файл с именем **Dockerfile. AMD64**и замените его содержимое следующим:</span><span class="sxs-lookup"><span data-stu-id="aa581-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="aa581-371">Щелкните правой кнопкой мыши папку, расположенную под названием **модули** (она будет иметь имя, указанное ранее). в примере ниже он называется *писонмодуле*) и щелкните **создать папку**.</span><span class="sxs-lookup"><span data-stu-id="aa581-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="aa581-372">Назовите папку **Images**.</span><span class="sxs-lookup"><span data-stu-id="aa581-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="aa581-373">Внутри папки добавьте несколько изображений, содержащих мышь или клавиатуру.</span><span class="sxs-lookup"><span data-stu-id="aa581-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="aa581-374">Это будут образы, которые будут анализироваться моделью Tensorflow.</span><span class="sxs-lookup"><span data-stu-id="aa581-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="aa581-375">Если вы используете собственную модель, необходимо изменить ее, чтобы она отражала собственные данные моделей.</span><span class="sxs-lookup"><span data-stu-id="aa581-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="aa581-376">Теперь необходимо получить файлы **labels. txt** и **model. Pb** из папки Model, которая была ранее скачана (или создана на основе собственного **Пользовательская служба визуального распознавания**) в [главе 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="aa581-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="aa581-377">Создав файлы, поместите их в свое решение вместе с другими файлами.</span><span class="sxs-lookup"><span data-stu-id="aa581-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="aa581-378">Окончательный результат должен выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="aa581-378">The final result should look like the image below:</span></span>

    ![Создание контейнера](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="aa581-380">Глава 9. Упаковка решения в качестве контейнера</span><span class="sxs-lookup"><span data-stu-id="aa581-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="aa581-381">Теперь вы можете «упаковать» файлы в контейнер и отправить их в **Реестр контейнеров Azure**.</span><span class="sxs-lookup"><span data-stu-id="aa581-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="aa581-382">В VS Code откройте *интегрированный терминал* (**Просмотрите** > **встроенный терминал** или **CTRL**+ **\`** ) и используйте следующую строку для входа в **DOCKER** (замените значения команды на учетные данные **реестра контейнеров Azure (запись контроля доступа)** :</span><span class="sxs-lookup"><span data-stu-id="aa581-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="aa581-383">Щелкните правой кнопкой мыши файл **Deployment. Template. JSON**и выберите **Build IOT Edge Solution**.</span><span class="sxs-lookup"><span data-stu-id="aa581-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="aa581-384">Этот процесс сборки занимает довольно много времени (в зависимости от устройства), поэтому будьте готовы к ожиданию.</span><span class="sxs-lookup"><span data-stu-id="aa581-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="aa581-385">После завершения процесса сборки файл **Deployment. JSON** будет создан в новой папке с именем **config**.</span><span class="sxs-lookup"><span data-stu-id="aa581-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![создать развертывание](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="aa581-387">Снова откройте **палитру команд** и выполните поиск по запросу **Azure: вход**.</span><span class="sxs-lookup"><span data-stu-id="aa581-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="aa581-388">Следуйте инструкциям на экране, используя учетные данные учетной записи Azure. VS Code предоставит возможность *копирования и открытия*, которая скопирует код устройства, который вскоре потребуется, и откройте веб-браузер по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="aa581-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="aa581-389">При появлении запроса вставьте код устройства, чтобы проверить подлинность компьютера.</span><span class="sxs-lookup"><span data-stu-id="aa581-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![копирование и открытие](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="aa581-391">После входа вы увидите, что в нижней части панели " *Обзор* " находится новый раздел под названием **устройства центра Интернета вещей Azure**.</span><span class="sxs-lookup"><span data-stu-id="aa581-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="aa581-392">Щелкните этот раздел, чтобы развернуть его.</span><span class="sxs-lookup"><span data-stu-id="aa581-392">Click this section to expand it.</span></span>

    ![Пограничное устройство](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="aa581-394">Если устройство не указано здесь, необходимо щелкнуть правой кнопкой мыши узел *устройства центра Интернета вещей Azure*и выбрать команду **задать строку подключения центра Интернета вещей**.</span><span class="sxs-lookup"><span data-stu-id="aa581-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="aa581-395">Вы увидите, что **Палитра команд** (в верхней части VS Code) предложит ввести *строку подключения*.</span><span class="sxs-lookup"><span data-stu-id="aa581-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="aa581-396">Это *строка подключения* , записанная в конце [главы 3](#chapter-3---the-iot-hub-service).</span><span class="sxs-lookup"><span data-stu-id="aa581-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="aa581-397">После копирования строки в используйте клавишу **Ввод** .</span><span class="sxs-lookup"><span data-stu-id="aa581-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="aa581-398">Устройство должно быть загружено и отображено.</span><span class="sxs-lookup"><span data-stu-id="aa581-398">Your device should load, and appear.</span></span> <span data-ttu-id="aa581-399">Щелкните правой кнопкой мыши имя устройства и выберите пункт **Создать развертывание для одного устройства**.</span><span class="sxs-lookup"><span data-stu-id="aa581-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![создать развертывание](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="aa581-401">Появится командная строка *проводника* , где можно перейти к папке **config** , а затем выбрать файл **Deployment. JSON** .</span><span class="sxs-lookup"><span data-stu-id="aa581-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="aa581-402">Выбрав этот файл, нажмите кнопку **Выбор манифеста развертывания ребра** .</span><span class="sxs-lookup"><span data-stu-id="aa581-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![создать развертывание](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="aa581-404">На этом этапе вы предоставили **службе центра Интернета вещей** манифест, чтобы развернуть контейнер в качестве модуля из **реестра контейнеров Azure**, эффективно развертывая его на устройстве.</span><span class="sxs-lookup"><span data-stu-id="aa581-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="aa581-405">Чтобы просмотреть сообщения, отправленные с устройства в центр Интернета вещей, щелкните правой кнопкой мыши имя устройства в разделе **устройства центра Интернета вещей Azure** и в панели **обозревателя** щелкните **Start Monitoring D2C Message**.</span><span class="sxs-lookup"><span data-stu-id="aa581-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="aa581-406">Сообщения, отправляемые с устройства, должны появиться в окне терминала VS.</span><span class="sxs-lookup"><span data-stu-id="aa581-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="aa581-407">Подождите, так как это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="aa581-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="aa581-408">Сведения об отладке и проверке успешности развертывания см. в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="aa581-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="aa581-409">Теперь этот модуль будет перебирать изображения в папке **Images** и анализировать их с каждой итерацией.</span><span class="sxs-lookup"><span data-stu-id="aa581-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="aa581-410">Очевидно, что это лишь демонстрация того, как получить базовую модель машинного обучения для работы в среде IoT Edge устройства.</span><span class="sxs-lookup"><span data-stu-id="aa581-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="aa581-411">Чтобы расширить функциональные возможности этого примера, можно выполнить несколько способов.</span><span class="sxs-lookup"><span data-stu-id="aa581-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="aa581-412">Один из них может включать в себя некоторый код в контейнере, который фиксирует фотографии с веб-камеры, подключенной к устройству, и сохраняет изображения в папке Images.</span><span class="sxs-lookup"><span data-stu-id="aa581-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="aa581-413">Другой способ — скопировать образы с устройства IoT в контейнер.</span><span class="sxs-lookup"><span data-stu-id="aa581-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="aa581-414">Для этого можно выполнить следующую команду в терминале устройства IoT (возможно, небольшое приложение может выполнить задание, если вы захотите автоматизировать процесс).</span><span class="sxs-lookup"><span data-stu-id="aa581-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="aa581-415">Эту команду можно проверить, запустив ее вручную из расположения папки, в которой хранятся файлы:</span><span class="sxs-lookup"><span data-stu-id="aa581-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="aa581-416">Глава 10-Отладка среды выполнения IoT Edge</span><span class="sxs-lookup"><span data-stu-id="aa581-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="aa581-417">Ниже приведен список командных строк и советов, помогающих отслеживать и отлаживать действия по обмену сообщениями со *средой выполнения IOT Edge*на **устройстве Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="aa581-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="aa581-418">Проверьте состояние *среды выполнения IOT Edge* , выполнив следующую командную строку:</span><span class="sxs-lookup"><span data-stu-id="aa581-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="aa581-419">Не забудьте нажать клавиши **CTRL + C**, чтобы завершить Просмотр состояния.</span><span class="sxs-lookup"><span data-stu-id="aa581-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="aa581-420">Перечислите уже развернутые контейнеры.</span><span class="sxs-lookup"><span data-stu-id="aa581-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="aa581-421">Если *Служба центра Интернета вещей* успешно развернула контейнеры, они будут отображены с помощью следующей командной строки:</span><span class="sxs-lookup"><span data-stu-id="aa581-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="aa581-422">или</span><span class="sxs-lookup"><span data-stu-id="aa581-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="aa581-423">Приведенный выше вариант — хороший способ проверить, успешно ли развернут ваш модуль, так как он появится в списке. в противном случае вы увидите **только** *edgeHub* и *edgeAgent*.</span><span class="sxs-lookup"><span data-stu-id="aa581-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="aa581-424">Чтобы отобразить журналы кода контейнера, выполните следующую командную строку:</span><span class="sxs-lookup"><span data-stu-id="aa581-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="aa581-425">**Полезные команды для управления средой выполнения IoT Edge:**</span><span class="sxs-lookup"><span data-stu-id="aa581-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="aa581-426">Чтобы удалить все контейнеры на узле, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="aa581-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="aa581-427">Чтобы прерывать работу *IOT Edge среды выполнения*:</span><span class="sxs-lookup"><span data-stu-id="aa581-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="aa581-428">Глава 11. Создание службы таблиц</span><span class="sxs-lookup"><span data-stu-id="aa581-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="aa581-429">Вернитесь на портал Azure, где вы создадите службу таблиц Azure, создав ресурс хранилища.</span><span class="sxs-lookup"><span data-stu-id="aa581-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="aa581-430">Если вы еще не вошли в систему, войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="aa581-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="aa581-431">После входа в систему щелкните **создать ресурс**в верхнем левом углу и найдите **учетную запись хранения**и нажмите клавишу **Ввод** , чтобы начать поиск.</span><span class="sxs-lookup"><span data-stu-id="aa581-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="aa581-432">После появления щелкните **учетная запись хранения — BLOB-объект, файл, таблица и очередь** из списка.</span><span class="sxs-lookup"><span data-stu-id="aa581-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Поиск учетной записи хранения](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="aa581-434">На новой странице будет представлено описание службы **учетной записи хранения** .</span><span class="sxs-lookup"><span data-stu-id="aa581-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="aa581-435">В нижнем левом углу этого запроса нажмите кнопку **создать** , чтобы создать экземпляр этой службы.</span><span class="sxs-lookup"><span data-stu-id="aa581-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="aa581-437">После нажатия кнопки **создать**появится панель:</span><span class="sxs-lookup"><span data-stu-id="aa581-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="aa581-438">Вставьте нужное **имя** для этого экземпляра службы (*необходимо указать все символы в нижнем регистре*).</span><span class="sxs-lookup"><span data-stu-id="aa581-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="aa581-439">В качестве **модели развертывания**щелкните **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="aa581-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="aa581-440">Для **типа учетной записи**в раскрывающемся меню выберите пункт **хранилище (общее назначение**версии 1).</span><span class="sxs-lookup"><span data-stu-id="aa581-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="aa581-441">Щелкните соответствующее **Расположение**.</span><span class="sxs-lookup"><span data-stu-id="aa581-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="aa581-442">В раскрывающемся меню **репликация** щелкните **доступ для чтения — геоизбыточное хранилище (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="aa581-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="aa581-443">Для **повышения производительности**щелкните **стандартный**.</span><span class="sxs-lookup"><span data-stu-id="aa581-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="aa581-444">В разделе **Обязательное безопасное перемещение** щелкните **отключено**.</span><span class="sxs-lookup"><span data-stu-id="aa581-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="aa581-445">В раскрывающемся меню **подписки** выберите подходящую подписку.</span><span class="sxs-lookup"><span data-stu-id="aa581-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="aa581-446">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="aa581-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="aa581-447">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки и управления выставлением счетов за сбор ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="aa581-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="aa581-448">Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aa581-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="aa581-449">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="aa581-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="aa581-450">Оставьте **виртуальные сети** **отключенными**, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="aa581-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="aa581-451">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="aa581-451">Click **Create**.</span></span>

        ![Заполнение сведений о хранилище](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="aa581-453">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="aa581-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="aa581-454">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="aa581-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="aa581-455">Щелкните уведомления, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="aa581-455">Click on the notifications to explore your new Service instance.</span></span>

    ![уведомление о новом хранилище](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="aa581-457">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, и вы будете перенаправлены на новую страницу обзора экземпляра службы хранилища.</span><span class="sxs-lookup"><span data-stu-id="aa581-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![Переход к ресурсу](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="aa581-459">На странице Обзор в правой части щелкните **таблицы**.</span><span class="sxs-lookup"><span data-stu-id="aa581-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![таблице](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="aa581-461">Панель справа изменится на отображение сведений о **службе таблиц** , где необходимо добавить новую таблицу.</span><span class="sxs-lookup"><span data-stu-id="aa581-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="aa581-462">Для этого нажмите кнопку **+ Table (+ таблица** ) в левом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="aa581-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![Открытие таблиц](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="aa581-464">Будет отображена новая страница, где необходимо ввести **имя таблицы**.</span><span class="sxs-lookup"><span data-stu-id="aa581-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="aa581-465">Это имя, которое будет использоваться для ссылки на данные в приложении в последующих главах (создание приложение-функция и Power BI).</span><span class="sxs-lookup"><span data-stu-id="aa581-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="aa581-466">В качестве имени вставьте **иотмессажес** (вы можете выбрать собственное, просто запомните его, если оно используется далее в этом документе) и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="aa581-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="aa581-467">После создания новой таблицы ее можно будет увидеть на странице **службы таблиц** (в нижней части).</span><span class="sxs-lookup"><span data-stu-id="aa581-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![создана новая таблица](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="aa581-469">Теперь щелкните **ключи доступа** и создайте копию имени и **ключа** **учетной записи хранения** (с помощью Блокнота). Эти значения будут использоваться далее в этом курсе при создании **приложение-функция Azure**.</span><span class="sxs-lookup"><span data-stu-id="aa581-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![создана новая таблица](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="aa581-471">Снова с помощью панели слева перейдите к разделу *Служба таблиц* и щелкните **таблицы** (или **Обзор таблиц**в новых порталах) и скопируйте **URL-адрес таблицы** (с помощью Блокнота).</span><span class="sxs-lookup"><span data-stu-id="aa581-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="aa581-472">Это значение будет использоваться далее в этом курсе при связывании таблицы с приложением **Power BI** .</span><span class="sxs-lookup"><span data-stu-id="aa581-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![создана новая таблица](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="aa581-474">Глава 12. Заполнение таблицы Azure</span><span class="sxs-lookup"><span data-stu-id="aa581-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="aa581-475">Теперь, когда учетная запись хранения **службы таблиц** была настроена, можно добавить в нее данные, которые будут использоваться для хранения и извлечения информации.</span><span class="sxs-lookup"><span data-stu-id="aa581-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="aa581-476">Редактирование таблиц можно выполнить с помощью **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="aa581-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="aa581-477">Откройте **Visual Studio** (**не** Visual Studio Code).</span><span class="sxs-lookup"><span data-stu-id="aa581-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="aa581-478">В меню щелкните **View** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="aa581-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![открыть Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="aa581-480">**Cloud Explorer** откроется как закрепленный элемент (подождите, так как загрузка может занять некоторое время).</span><span class="sxs-lookup"><span data-stu-id="aa581-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="aa581-481">Если подписка, использованная для создания *учетных записей хранения* , не отображается, убедитесь, что у вас есть:</span><span class="sxs-lookup"><span data-stu-id="aa581-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="aa581-482">Войдите в ту же учетную запись, которая использовалась для портала Azure.</span><span class="sxs-lookup"><span data-stu-id="aa581-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="aa581-483">Выберите подписку на странице управления учетными записями (может потребоваться применить фильтр из параметров учетной записи):</span><span class="sxs-lookup"><span data-stu-id="aa581-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![Найти подписку](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="aa581-485">Будут показаны облачные службы Azure.</span><span class="sxs-lookup"><span data-stu-id="aa581-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="aa581-486">Найдите **учетные записи хранения** и щелкните стрелку слева от нее, чтобы развернуть учетные записи.</span><span class="sxs-lookup"><span data-stu-id="aa581-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Открытие учетных записей хранения](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="aa581-488">После развертывания вновь созданная **учетная запись хранения** должна быть доступна.</span><span class="sxs-lookup"><span data-stu-id="aa581-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="aa581-489">Щелкните стрелку слева от хранилища, а затем после разворачивания найдите **таблицы** и щелкните стрелку рядом с ней, чтобы открыть **таблицу** , созданную в последней главе.</span><span class="sxs-lookup"><span data-stu-id="aa581-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="aa581-490">Дважды щелкните **таблицу**.</span><span class="sxs-lookup"><span data-stu-id="aa581-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="aa581-491">Таблица откроется в центре окна Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa581-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="aa581-492">Щелкните значок таблицы с **+** (плюс).</span><span class="sxs-lookup"><span data-stu-id="aa581-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![Добавить новую таблицу](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="aa581-494">Появится окно с запросом на *Добавление сущности*.</span><span class="sxs-lookup"><span data-stu-id="aa581-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="aa581-495">Вы создадите только одну сущность, хотя она будет иметь три свойства.</span><span class="sxs-lookup"><span data-stu-id="aa581-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="aa581-496">Вы увидите, что *PartitionKey* и *RowKey* уже предоставлены, так как они используются таблицей для поиска данных.</span><span class="sxs-lookup"><span data-stu-id="aa581-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![ключ секции и строки](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="aa581-498">Обновите следующие значения:</span><span class="sxs-lookup"><span data-stu-id="aa581-498">Update the following values:</span></span>

    - <span data-ttu-id="aa581-499">Имя: **PartitionKey**, значение: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="aa581-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="aa581-500">Имя: **RowKey**, значение: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="aa581-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="aa581-501">Затем щелкните **Добавить свойство** (в левом нижнем углу окна *добавить сущность* ) и добавьте следующее свойство:</span><span class="sxs-lookup"><span data-stu-id="aa581-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="aa581-502">**Мессажеконтент**в виде *строки*оставьте значение пустым.</span><span class="sxs-lookup"><span data-stu-id="aa581-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="aa581-503">Таблица должна соответствовать таблице, показанной на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="aa581-503">Your table should match the one in the image below:</span></span>

    ![добавить правильные значения](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="aa581-505">Причина, по которой сущность имеет номер 1 в ключе строки, — это потому, что может потребоваться добавить дополнительные сообщения, если вы хотите поэкспериментировать с этим курсом.</span><span class="sxs-lookup"><span data-stu-id="aa581-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="aa581-506">По завершении нажмите кнопку **ОК** .</span><span class="sxs-lookup"><span data-stu-id="aa581-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="aa581-507">Теперь таблица готова к использованию.</span><span class="sxs-lookup"><span data-stu-id="aa581-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="aa581-508">Глава 13. Создание приложение-функция Azure</span><span class="sxs-lookup"><span data-stu-id="aa581-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="aa581-509">Теперь пришло время создать *приложение-функция Azure*, который будет вызываться *службой центра Интернета вещей* для хранения сообщений *IOT Edge* устройства в службе **таблиц** , созданной в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="aa581-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="aa581-510">Сначала необходимо создать файл, который позволит вашей функции Azure загружать нужные библиотеки.</span><span class="sxs-lookup"><span data-stu-id="aa581-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="aa581-511">Откройте **Блокнот** (нажмите клавишу *Windows*и введите *Блокнот*).</span><span class="sxs-lookup"><span data-stu-id="aa581-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![открыть Блокнот](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="aa581-513">При открытии блокнота вставьте в него структуру JSON.</span><span class="sxs-lookup"><span data-stu-id="aa581-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="aa581-514">После этого сохраните его на рабочем столе как **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="aa581-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="aa581-515">Этот файл определяет библиотеки, которые будет использовать функция.</span><span class="sxs-lookup"><span data-stu-id="aa581-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="aa581-516">Если вы использовали NuGet, он покажется знакомым.</span><span class="sxs-lookup"><span data-stu-id="aa581-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="aa581-517">Важно, чтобы именование было правильным; Убедитесь, что у него нет расширения файла **. txt** .</span><span class="sxs-lookup"><span data-stu-id="aa581-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="aa581-518">Ниже приведены справочные сведения.</span><span class="sxs-lookup"><span data-stu-id="aa581-518">See below for reference:</span></span>
    >
    > ![Сохранение JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="aa581-520">Войдите на [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="aa581-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="aa581-521">После входа в систему щелкните **создать ресурс** в верхнем левом углу и выполните поиск по запросу **приложение-функция**и нажмите клавишу **Ввод** , чтобы выполнить поиск.</span><span class="sxs-lookup"><span data-stu-id="aa581-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="aa581-522">Щелкните *приложение-функция* из результатов, чтобы открыть новую панель.</span><span class="sxs-lookup"><span data-stu-id="aa581-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![Поиск приложения функции](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="aa581-524">На новой панели будет представлено описание службы **приложение-функция** .</span><span class="sxs-lookup"><span data-stu-id="aa581-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="aa581-525">В нижнем левом углу этой панели нажмите кнопку " **создать** ", чтобы создать связь с этой службой.</span><span class="sxs-lookup"><span data-stu-id="aa581-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![экземпляр приложения функции](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="aa581-527">После нажатия кнопки **создать**заполните следующие поля:</span><span class="sxs-lookup"><span data-stu-id="aa581-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="aa581-528">В качестве **имени приложения**вставьте нужное имя для этого экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="aa581-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="aa581-529">Выберите **подписку**.</span><span class="sxs-lookup"><span data-stu-id="aa581-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="aa581-530">Выберите ценовую категорию, подходящую для вас. Если вы впервые создаете **службу приложение-функция**, вам будет доступен бесплатный уровень.</span><span class="sxs-lookup"><span data-stu-id="aa581-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="aa581-531">Выберите **группу ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="aa581-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="aa581-532">Группа ресурсов предоставляет способ мониторинга, контроля доступа, подготовки и управления выставлением счетов за сбор ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="aa581-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="aa581-533">Рекомендуется размещать все службы Azure, связанные с одним проектом (например, такие курсы), в общей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="aa581-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="aa581-534">Если вы хотите ознакомиться с дополнительными сведениями о группах ресурсов Azure, перейдите [по этой ссылке, чтобы управлять группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="aa581-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="aa581-535">Для **ОС**щелкните Windows, так как это Целевая платформа.</span><span class="sxs-lookup"><span data-stu-id="aa581-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="aa581-536">Выберите **план размещения** (в этом учебнике используется **план потребления**).</span><span class="sxs-lookup"><span data-stu-id="aa581-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="aa581-537">Выберите **Расположение** (выберите то же расположение, что и хранилище, созданное на предыдущем шаге).</span><span class="sxs-lookup"><span data-stu-id="aa581-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="aa581-538">В разделе **хранилище** **необходимо выбрать службу хранилища, созданную на предыдущем шаге**.</span><span class="sxs-lookup"><span data-stu-id="aa581-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="aa581-539">Вам не потребуется *Application Insights* в этом приложении, поэтому вы можете **оставить его без**изменений.</span><span class="sxs-lookup"><span data-stu-id="aa581-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="aa581-540">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="aa581-540">Click **Create**.</span></span>

        ![создать новый экземпляр](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="aa581-542">После нажатия кнопки **создать**необходимо подождать, пока не будет создана служба, а это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="aa581-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="aa581-543">После создания экземпляра службы на портале отобразится уведомление.</span><span class="sxs-lookup"><span data-stu-id="aa581-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![новое уведомление](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="aa581-545">Щелкните уведомление, когда развертывание завершится успешно (завершено).</span><span class="sxs-lookup"><span data-stu-id="aa581-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="aa581-546">Нажмите кнопку " **Переход к ресурсу** " в уведомлении, чтобы изучить новый экземпляр службы.</span><span class="sxs-lookup"><span data-stu-id="aa581-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Переход к ресурсу](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="aa581-548">В левой части новой панели щелкните значок **+** (плюс) рядом с пунктом *функции*, чтобы создать новую функцию.</span><span class="sxs-lookup"><span data-stu-id="aa581-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![Добавить новую функцию](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="aa581-550">На центральной панели появится окно создания **функции** .</span><span class="sxs-lookup"><span data-stu-id="aa581-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="aa581-551">Прокрутите вниз и щелкните **Пользовательская функция**.</span><span class="sxs-lookup"><span data-stu-id="aa581-551">Scroll down further, and click on **Custom function**.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="aa581-553">Прокрутите страницу вниз до пункта **центр Интернета вещей (концентратор событий)** , а затем щелкните его.</span><span class="sxs-lookup"><span data-stu-id="aa581-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="aa581-555">В колонке центр **Интернета вещей (концентратор событий)** задайте для **C#** параметра язык значение и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="aa581-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="aa581-557">В окне, которое появится, убедитесь, что выбран **центр Интернета вещей** , а имя поля *центр Интернета* вещей соответствует имени созданной ранее *службы центра Интернета вещей* ([на шаге 8 главы 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="aa581-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="aa581-558">Затем нажмите кнопку **выбрать** .</span><span class="sxs-lookup"><span data-stu-id="aa581-558">Then click the **Select** button.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="aa581-560">Вернитесь в колонку **центр Интернета вещей (концентратор событий)** и щелкните **создать**.</span><span class="sxs-lookup"><span data-stu-id="aa581-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="aa581-562">Вы будете перенаправлены в редактор функций.</span><span class="sxs-lookup"><span data-stu-id="aa581-562">You will be redirected to the function editor.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="aa581-564">Удалите весь код в нем и замените его следующим:</span><span class="sxs-lookup"><span data-stu-id="aa581-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="aa581-565">Измените следующие переменные, чтобы они соответствовали соответствующим значениям (значения**таблицы** и **хранилища** , начиная с [шага 11 и 13, соответственно, из раздела 11](#chapter-11---create-table-service)), которые будут находиться в вашей **учетной записи хранения**:</span><span class="sxs-lookup"><span data-stu-id="aa581-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="aa581-566">**TableName**с именем **таблицы** , расположенной в вашей **учетной записи хранения**.</span><span class="sxs-lookup"><span data-stu-id="aa581-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="aa581-567">**таблеурл**с URL-адресом **таблицы** , расположенной в вашей **учетной записи хранения**.</span><span class="sxs-lookup"><span data-stu-id="aa581-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="aa581-568">**storageAccountName**, указав имя значения, соответствующее имени **учетной записи хранения** .</span><span class="sxs-lookup"><span data-stu-id="aa581-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="aa581-569">**storageAccountKey**с ключом, полученным в ранее созданной службе хранилища.</span><span class="sxs-lookup"><span data-stu-id="aa581-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="aa581-571">После ввода кода нажмите кнопку **сохранить**.</span><span class="sxs-lookup"><span data-stu-id="aa581-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="aa581-572">Затем щелкните значок **\<** (стрелка) в правой части страницы.</span><span class="sxs-lookup"><span data-stu-id="aa581-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="aa581-574">Панель будет продвигаться справа.</span><span class="sxs-lookup"><span data-stu-id="aa581-574">A panel will slide in from the right.</span></span> <span data-ttu-id="aa581-575">На этой панели нажмите кнопку **Отправить**и отобразится *Обозреватель файлов* .</span><span class="sxs-lookup"><span data-stu-id="aa581-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="aa581-576">Перейдите к и щелкните файл **Project. JSON** , созданный ранее в **блокноте** , а затем нажмите кнопку **Открыть** .</span><span class="sxs-lookup"><span data-stu-id="aa581-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="aa581-577">Этот файл определяет библиотеки, которые будет использовать функция.</span><span class="sxs-lookup"><span data-stu-id="aa581-577">This file defines the libraries that your function will use.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="aa581-579">После отправки файл появится на панели справа.</span><span class="sxs-lookup"><span data-stu-id="aa581-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="aa581-580">Щелкнув его, вы откроете его в редакторе **функций** .</span><span class="sxs-lookup"><span data-stu-id="aa581-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="aa581-581">Он должен выглядеть **точно** так же, как и следующий образ.</span><span class="sxs-lookup"><span data-stu-id="aa581-581">It must look **exactly** the same as the next image.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="aa581-583">На этом этапе было бы неплохо протестировать возможности функции для хранения сообщения в *таблице*.</span><span class="sxs-lookup"><span data-stu-id="aa581-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="aa581-584">В правой верхней части окна щелкните **тест**.</span><span class="sxs-lookup"><span data-stu-id="aa581-584">On the top right side of the window, click on **Test**.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="aa581-586">Вставьте сообщение в **текст запроса**, как показано на рисунке выше, и щелкните **Run (выполнить**).</span><span class="sxs-lookup"><span data-stu-id="aa581-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="aa581-587">Функция будет запущена, отображая состояние результата (вы увидите зеленое **состояние 202**, расположенное выше окна *вывод* , что означает успешный вызов):</span><span class="sxs-lookup"><span data-stu-id="aa581-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![результат вывода](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="aa581-589">Глава 14. Просмотр активных сообщений</span><span class="sxs-lookup"><span data-stu-id="aa581-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="aa581-590">Если теперь открыть Visual Studio (**не** Visual Studio Code), вы можете визуализировать результат тестового сообщения, так как он будет храниться в области строк *мессажеконтент* .</span><span class="sxs-lookup"><span data-stu-id="aa581-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![Пользовательская функция](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="aa581-592">После того как служба таблиц и приложение-функция на месте, в таблице *иотмессажес* будут отображаться сообщения устройства Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="aa581-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="aa581-593">Если оно еще не запущено, запустите устройство еще раз, и вы сможете просматривать сообщения о результатах с устройства и модуля в таблице с помощью Visual Studio *Cloud Explorer*.</span><span class="sxs-lookup"><span data-stu-id="aa581-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![Визуализация данных](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="aa581-595">Глава 15-Power BIная установка</span><span class="sxs-lookup"><span data-stu-id="aa581-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="aa581-596">Для визуализации данных с вашего устройства Интернета вещей, которое будет настроено **Power BI** (версия для настольной системы), можно получить данные из только что созданной службы *таблиц* .</span><span class="sxs-lookup"><span data-stu-id="aa581-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="aa581-597">Затем версия *HoloLens* Power BI будет использовать эти данные для визуализации результата.</span><span class="sxs-lookup"><span data-stu-id="aa581-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="aa581-598">Откройте Microsoft Store в Windows 10 и выполните поиск **Power BI Desktop**.</span><span class="sxs-lookup"><span data-stu-id="aa581-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="aa581-600">Скачайте приложение.</span><span class="sxs-lookup"><span data-stu-id="aa581-600">Download the application.</span></span> <span data-ttu-id="aa581-601">После завершения загрузки откройте его.</span><span class="sxs-lookup"><span data-stu-id="aa581-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="aa581-602">Войдите в *Power BI* с помощью **учетной записи Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="aa581-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="aa581-603">Чтобы зарегистрироваться, вы можете перенаправлены в браузер.</span><span class="sxs-lookup"><span data-stu-id="aa581-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="aa581-604">После регистрации вернитесь в приложение Power BI и снова выполните вход.</span><span class="sxs-lookup"><span data-stu-id="aa581-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="aa581-605">Щелкните **получить данные** , а затем — **еще...** .</span><span class="sxs-lookup"><span data-stu-id="aa581-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="aa581-607">Щелкните **Azure**, **хранилище таблиц Azure**, а затем щелкните **подключить**.</span><span class="sxs-lookup"><span data-stu-id="aa581-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="aa581-609">При создании службы таблиц вам будет предложено вставить **URL-адрес таблицы** , собранный ранее ([на шаге 13 главы 11](#chapter-11---create-table-service)).</span><span class="sxs-lookup"><span data-stu-id="aa581-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="aa581-610">После вставки URL-адреса удалите часть пути, ссылающуюся на таблицу "вложенную папку" (которая была Иотмессажес в этом курсе).</span><span class="sxs-lookup"><span data-stu-id="aa581-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="aa581-611">Окончательный результат должен отобразиться на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="aa581-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="aa581-612">Затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="aa581-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="aa581-614">При создании табличного хранилища вам будет предложено вставить указанный ранее **ключ к хранилищу** (см.[Шаг 11 главы 11](#chapter-11---create-table-service)).</span><span class="sxs-lookup"><span data-stu-id="aa581-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="aa581-615">Затем щелкните **подключить**.</span><span class="sxs-lookup"><span data-stu-id="aa581-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="aa581-617">Отобразится **Панель Навигатор** , установите флажок рядом с таблицей и щелкните **Load (загрузить**).</span><span class="sxs-lookup"><span data-stu-id="aa581-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="aa581-619">Таблица теперь загружена на Power BI, но для ее вывода требуется запрос.</span><span class="sxs-lookup"><span data-stu-id="aa581-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="aa581-620">Для этого щелкните правой кнопкой мыши имя таблицы, расположенное на **панели поля** в правой части экрана.</span><span class="sxs-lookup"><span data-stu-id="aa581-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="aa581-621">Затем щелкните **изменить запрос**.</span><span class="sxs-lookup"><span data-stu-id="aa581-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="aa581-623">**Редактор Power Query** откроется в виде нового окна, в котором отображается таблица.</span><span class="sxs-lookup"><span data-stu-id="aa581-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="aa581-624">Щелкните **запись** слова в столбце *содержимое* таблицы, чтобы визуализировать сохраненное содержимое.</span><span class="sxs-lookup"><span data-stu-id="aa581-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="aa581-626">Щелкните по **таблице**в левом верхнем углу окна.</span><span class="sxs-lookup"><span data-stu-id="aa581-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="aa581-628">Нажмите кнопку **закрыть & применить**.</span><span class="sxs-lookup"><span data-stu-id="aa581-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="aa581-630">Завершив загрузку запроса, на **панели «поля**» в правой части экрана заполните поля, соответствующие **имени** и **значению**параметров, чтобы визуализировать содержимое столбца **мессажеконтент** .</span><span class="sxs-lookup"><span data-stu-id="aa581-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="aa581-632">Щелкните значок " **синий диск** " в левом верхнем углу окна, чтобы сохранить свою работу в выбранной папке.</span><span class="sxs-lookup"><span data-stu-id="aa581-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="aa581-634">Теперь можно нажать кнопку Опубликовать, чтобы отправить таблицу в рабочую область.</span><span class="sxs-lookup"><span data-stu-id="aa581-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="aa581-635">При появлении запроса щелкните **Моя рабочая область** и нажмите кнопку *выбрать*.</span><span class="sxs-lookup"><span data-stu-id="aa581-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="aa581-636">Дождитесь, пока отобразится успешный результат отправки.</span><span class="sxs-lookup"><span data-stu-id="aa581-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="aa581-639">В следующей главе описывается только для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aa581-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="aa581-640">Power BI в настоящее время недоступна в качестве иммерсивного приложения, но вы можете запустить версию рабочего стола на портале Windows Mixed Reality (Клифф House) через классическое приложение.</span><span class="sxs-lookup"><span data-stu-id="aa581-640">Power BI is not currently available as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="aa581-641">Глава 16-отображение данных Power BI в HoloLens</span><span class="sxs-lookup"><span data-stu-id="aa581-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="aa581-642">В HoloLens Войдите в **Microsoft Store**, коснувшись его значка в списке приложений.</span><span class="sxs-lookup"><span data-stu-id="aa581-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="aa581-644">Найдите и скачайте приложение **Power BI** .</span><span class="sxs-lookup"><span data-stu-id="aa581-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="aa581-646">Запустите **Power BI** из списка приложений.</span><span class="sxs-lookup"><span data-stu-id="aa581-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="aa581-647">**Power BI** может попросить вас войти в **учетную запись Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="aa581-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="aa581-648">В пределах приложения Рабочая область должна отображаться по умолчанию, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="aa581-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="aa581-649">Если это не происходит, просто щелкните значок рабочей области в левой части окна.</span><span class="sxs-lookup"><span data-stu-id="aa581-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="aa581-651">Ваша работа над приложением центра Интернета вещей завершена</span><span class="sxs-lookup"><span data-stu-id="aa581-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="aa581-652">Поздравляем! вы успешно создали службу центра Интернета вещей с имитацией устройства с виртуальными машинами.</span><span class="sxs-lookup"><span data-stu-id="aa581-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="aa581-653">Устройство может передавать результаты модели машинного обучения в службу таблиц Azure, что облегчается приложение-функция Azure, которые считываются в Power BI и выводятся в виде визуализации в Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="aa581-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="aa581-655">Премиальные упражнения</span><span class="sxs-lookup"><span data-stu-id="aa581-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="aa581-656">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="aa581-656">Exercise 1</span></span>

<span data-ttu-id="aa581-657">Разверните структуру обмена сообщениями, хранящуюся в таблице, и отобразите ее в виде диаграммы.</span><span class="sxs-lookup"><span data-stu-id="aa581-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="aa581-658">Вам может потребоваться получить дополнительные данные и сохранить их в одной и той же таблице для последующего отображения.</span><span class="sxs-lookup"><span data-stu-id="aa581-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="aa581-659">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="aa581-659">Exercise 2</span></span>

<span data-ttu-id="aa581-660">Создайте дополнительный модуль "запись камеры" для развертывания на доске IoT, чтобы он мог записывать образы через камеру для анализа.</span><span class="sxs-lookup"><span data-stu-id="aa581-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
