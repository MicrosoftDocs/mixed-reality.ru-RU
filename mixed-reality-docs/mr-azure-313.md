---
title: Г-н и 313 - служба центра Интернета вещей Azure
description: Выполните этот курс, чтобы узнать, как реализовать службу центра Интернета вещей на виртуальной машине под управлением Ubuntu 16.4, а затем визуализировать данные сообщения с помощью Microsoft HoloLens или иммерсивных Гарнитура (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, смешанной реальности, academy, edge, edge Интернета вещей, руководство, api, уведомления, функции, таблицы, hololens, насыщенные, виртуальной реальности, Интернета, виртуальная машина, ubuntu, python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597569"
---
>[!NOTE]
><span data-ttu-id="c3368-104">Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.</span><span class="sxs-lookup"><span data-stu-id="c3368-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c3368-105">Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.</span><span class="sxs-lookup"><span data-stu-id="c3368-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c3368-106">Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3368-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c3368-107">Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах.</span><span class="sxs-lookup"><span data-stu-id="c3368-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c3368-108">Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3368-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c3368-109">Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.</span><span class="sxs-lookup"><span data-stu-id="c3368-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="c3368-110">Г-н и Azure 313: Служба центра Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="c3368-110">MR and Azure 313: IoT Hub Service</span></span>

![результат курс](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="c3368-112">В рамках этого курса вы узнаете, как реализовать **службы центра Интернета вещей** на виртуальной машине под управлением операционной системы Ubuntu 16.4.</span><span class="sxs-lookup"><span data-stu-id="c3368-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="c3368-113">**Приложение-функцию Azure** будет использоваться для получения сообщений из виртуальной Машине Ubuntu и сохранить результат в **службу таблиц Azure**.</span><span class="sxs-lookup"><span data-stu-id="c3368-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="c3368-114">Затем можно просматривать с помощью **Power BI** на Microsoft HoloLens или иммерсивных Гарнитура (VR).</span><span class="sxs-lookup"><span data-stu-id="c3368-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="c3368-115">Содержимое этого курса *применимо* на устройствах IoT Edge на то, что для целей этого курса, основное внимание будет уделено среде виртуальной машины, чтобы доступ к физическому устройству Edge не требуется.</span><span class="sxs-lookup"><span data-stu-id="c3368-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="c3368-116">Выполнив этот курс, вы узнаете следующее:</span><span class="sxs-lookup"><span data-stu-id="c3368-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="c3368-117">Развертывание **модуля IoT Edge** к виртуальной машине (Ubuntu 16 ОС), который будет представлять устройства Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="c3368-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="c3368-118">Добавить **модели Tensorflow Azure Custom Vision** в модуле Edge с кодом, который будет анализировать образы, хранящиеся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="c3368-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="c3368-119">Настройка модуля для отправки сообщения результата анализа обратно в ваш **службы центра Интернета вещей**.</span><span class="sxs-lookup"><span data-stu-id="c3368-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="c3368-120">Используйте **приложение-функцию Azure** для сохранения сообщения в **таблиц Azure**.</span><span class="sxs-lookup"><span data-stu-id="c3368-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="c3368-121">Настройка **Power BI** для сбора сохраненного сообщения и создать отчет.</span><span class="sxs-lookup"><span data-stu-id="c3368-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="c3368-122">Визуализируйте данные сообщения Интернета вещей в **Power BI**.</span><span class="sxs-lookup"><span data-stu-id="c3368-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="c3368-123">К службам, которые будут использоваться относятся:</span><span class="sxs-lookup"><span data-stu-id="c3368-123">The Services you will use include:</span></span>

- <span data-ttu-id="c3368-124">**Центр Интернета вещей Azure** — это служба Microsoft Azure, что позволяет разработчикам подключение, мониторинг и управление, ресурсов Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="c3368-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="c3368-125">Дополнительные сведения см. в статье [ **службы центра Интернета вещей** страницы](https://azure.microsoft.com/en-au/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="c3368-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="c3368-126">**Реестр контейнеров Azure** — это служба Microsoft Azure, которую разработчики могут хранить образы контейнеров, для различных типов контейнеров.</span><span class="sxs-lookup"><span data-stu-id="c3368-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="c3368-127">Дополнительные сведения см. в статье [ **службы реестра контейнеров Azure** страницы](https://azure.microsoft.com/en-au/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="c3368-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="c3368-128">**Azure приложения-функции** — служба Microsoft Azure, которая позволяет разработчикам запускать небольшие фрагменты кода, «», в функциях Azure.</span><span class="sxs-lookup"><span data-stu-id="c3368-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="c3368-129">Это позволяет делегировать работу в облаке, а не локального приложения, который может иметь множество преимуществ.</span><span class="sxs-lookup"><span data-stu-id="c3368-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="c3368-130">**Функции Azure** поддерживает несколько языков разработки, в том числе C\#, F\#, Node.js, Java и PHP.</span><span class="sxs-lookup"><span data-stu-id="c3368-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="c3368-131">Дополнительные сведения см. в статье [ **"функции Azure"** страницы](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="c3368-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="c3368-132">**Хранилище Azure: Таблицы** — это служба Microsoft Azure, которая позволяет разработчикам хранить структурированные, отличные от SQL, данные в облаке, сделаете его доступным для в любом месте.</span><span class="sxs-lookup"><span data-stu-id="c3368-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="c3368-133">Служба может похвастаться макета без схемы, позволяя развитие таблиц, при необходимости и таким образом обладает большой гибкостью.</span><span class="sxs-lookup"><span data-stu-id="c3368-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="c3368-134">Дополнительные сведения см. в статье [ **таблицы Azure** страницы](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="c3368-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="c3368-135">Этот курс поможет, как установить и использовать службы центра Интернета вещей и последующей визуализации ответ предоставлялся через устройство.</span><span class="sxs-lookup"><span data-stu-id="c3368-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="c3368-136">Это будет необходимо применение этих понятий для пользовательской установки службы центра Интернета вещей, возможно, вы разрабатываете.</span><span class="sxs-lookup"><span data-stu-id="c3368-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="c3368-137">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="c3368-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c3368-138">Курс</span><span class="sxs-lookup"><span data-stu-id="c3368-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c3368-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c3368-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c3368-140"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="c3368-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c3368-141">Г-н и Azure 313: Служба центра Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="c3368-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3368-142">✔️</span><span class="sxs-lookup"><span data-stu-id="c3368-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3368-143">✔️</span><span class="sxs-lookup"><span data-stu-id="c3368-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="c3368-144">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="c3368-144">Prerequisites</span></span>

<span data-ttu-id="c3368-145">Наиболее актуальные предварительные требования для разработки с помощью смешанной реальности, в том числе с Microsoft HoloLens, откройте страницу [установить средства](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) статьи.</span><span class="sxs-lookup"><span data-stu-id="c3368-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="c3368-146">Этот учебник предназначен для разработчиков, имеющих минимальный опыт с Python.</span><span class="sxs-lookup"><span data-stu-id="c3368-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="c3368-147">Также имейте в виду, что предварительные требования и инструкции в этом документе представляют новые были протестированы и проверены на момент написания статьи (июля 2018 г.).</span><span class="sxs-lookup"><span data-stu-id="c3368-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="c3368-148">Вы можете свободно использовать последнюю программное обеспечение, как указано в [установить средства](install-the-tools.md) статьи, то, что следует не полагать, что информация в этом курсе будет точным соответствием будет найти в новой версии по сравнению, перечисленных ниже.</span><span class="sxs-lookup"><span data-stu-id="c3368-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="c3368-149">Требуется следующее оборудование и программное обеспечение:</span><span class="sxs-lookup"><span data-stu-id="c3368-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="c3368-150">Windows 10 Fall Creators Update (или более поздней версии), **включен режим разработчика**</span><span class="sxs-lookup"><span data-stu-id="c3368-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="c3368-151">Невозможно запустить виртуальную машину с помощью Hyper-V в Windows 10 Home Edition.</span><span class="sxs-lookup"><span data-stu-id="c3368-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="c3368-152">Пакет SDK для Windows 10 (последняя версия)</span><span class="sxs-lookup"><span data-stu-id="c3368-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="c3368-153">A HoloLens **включен режим разработчика**</span><span class="sxs-lookup"><span data-stu-id="c3368-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="c3368-154">Visual Studio 2017.15.4 (используется только для доступа к Azure Cloud Explorer)</span><span class="sxs-lookup"><span data-stu-id="c3368-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="c3368-155">Доступ к Интернету для Azure, а также для службы центра Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="c3368-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="c3368-156">Дополнительные сведения, выполните инструкции из этого [ссылку на страницу службы центра Интернета вещей](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="c3368-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="c3368-157">Модель машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="c3368-157">A machine learning model.</span></span> <span data-ttu-id="c3368-158">Если у вас нет собственных, готовая к использованию модели [можно использовать модель, предоставляемую в этом курсе](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="c3368-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="c3368-159">**Hyper-V** включено на компьютере разработки Windows 10 по.</span><span class="sxs-lookup"><span data-stu-id="c3368-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="c3368-160">Виртуальной машине под управлением Ubuntu (16.4 или 18.4. в случае), работает на компьютере разработки или в качестве альтернативы можно использовать отдельный компьютер под управлением Linux (Ubuntu 16.4 или 18.4. в случае).</span><span class="sxs-lookup"><span data-stu-id="c3368-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="c3368-161">Можно найти дополнительные сведения о том, как создать виртуальную Машину в Windows с помощью Hyper-V в [«Перед началом работы» главы](#before-you-start). () https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="c3368-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="c3368-162">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="c3368-162">Before you start</span></span>

1. <span data-ttu-id="c3368-163">Настроить и проверить ваш HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3368-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="c3368-164">Если вам нужна поддерживает настройку вашей HoloLens [не забудьте посетить статье установки HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="c3368-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="c3368-165">Рекомендуется выполнять **калибровки** и **настройке датчика** начале разработке нового приложения HoloLens (иногда удобнее для выполнения этих задач для каждого пользователя).</span><span class="sxs-lookup"><span data-stu-id="c3368-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="c3368-166">Получить справку по калибровки, выполните инструкции из этого [ссылка на статью калибровки HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="c3368-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="c3368-167">Справочные сведения о настройке датчика, выполните инструкции из этого [ссылка на статью о настройке датчика HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="c3368-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="c3368-168">Настройка вашей **виртуальной машины Ubuntu** с помощью **Hyper-V**.</span><span class="sxs-lookup"><span data-stu-id="c3368-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="c3368-169">Следующие ресурсы помогут вам в процессе.</span><span class="sxs-lookup"><span data-stu-id="c3368-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="c3368-170">Во-первых, перейдите по ссылке для [загрузить ISO-образ Ubuntu 16.04.4 LTS (Xenial Xerus)](http://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="c3368-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="c3368-171">Выберите **образа настольной системы ПК (AMD64) 64-разрядных**.</span><span class="sxs-lookup"><span data-stu-id="c3368-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="c3368-172">Убедитесь, что **Hyper-V** включена на компьютере Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c3368-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="c3368-173">Перейдите по этой ссылке рекомендации [Установка и включение Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="c3368-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="c3368-174">Запустите Hyper-V и создайте новую виртуальную Машину Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="c3368-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="c3368-175">Перейдите по этой ссылке для [Поэтапное руководство о том, как создать виртуальную Машину с Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="c3368-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="c3368-176">При запросе к **«Установить операционную систему из файла загрузочного образа»** выберите **Ubuntu ISO** у вас есть загрузки ранее.</span><span class="sxs-lookup"><span data-stu-id="c3368-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c3368-177">С помощью **Hyper-V быстрое создание** не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c3368-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="c3368-178">Глава 1 - извлечь Custom Vision модель</span><span class="sxs-lookup"><span data-stu-id="c3368-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="c3368-179">В этом курсе вы получите доступ к [предварительно созданные модели Custom Vision](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) , обнаруживает клавиатуры и мыши из образов.</span><span class="sxs-lookup"><span data-stu-id="c3368-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="c3368-180">Если вы используете это, перейдите к разделу [Глава 2](#chapter-2---the-container-registry-service).</span><span class="sxs-lookup"><span data-stu-id="c3368-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="c3368-181">Тем не менее если вы хотите использовать собственную модель Custom Vision можно выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="c3368-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="c3368-182">В вашей **Custom Vision проекта** перейдите **производительности** вкладки.</span><span class="sxs-lookup"><span data-stu-id="c3368-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="c3368-183">Необходимо использовать модель *compact* домена, для экспорта модели.</span><span class="sxs-lookup"><span data-stu-id="c3368-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="c3368-184">Можно изменить модели домена в параметрах проекта.</span><span class="sxs-lookup"><span data-stu-id="c3368-184">You can change your models domain in the settings for your project.</span></span>

    ![Вкладка "производительность"](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="c3368-186">Выберите **итерации** вы хотите экспортировать и щелкнуть **Экспорт**.</span><span class="sxs-lookup"><span data-stu-id="c3368-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="c3368-187">Появится колонка.</span><span class="sxs-lookup"><span data-stu-id="c3368-187">A blade will appear.</span></span>

    ![колонка "Экспорт"](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="c3368-189">В колонке щелкните **файл Docker**.</span><span class="sxs-lookup"><span data-stu-id="c3368-189">In the blade click **Docker File**.</span></span>

    ![Выберите docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="c3368-191">Нажмите кнопку **Linux** в раскрывающемся меню и затем щелкните на **загрузить**.</span><span class="sxs-lookup"><span data-stu-id="c3368-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Щелкните "скачать"](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="c3368-193">Распакуйте содержимое.</span><span class="sxs-lookup"><span data-stu-id="c3368-193">Unzip the content.</span></span> <span data-ttu-id="c3368-194">Он понадобится позже в этом курсе.</span><span class="sxs-lookup"><span data-stu-id="c3368-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="c3368-195">Глава 2 - службе реестра контейнеров</span><span class="sxs-lookup"><span data-stu-id="c3368-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="c3368-196">**Службы реестра контейнеров** — это репозиторий, используемого для размещения контейнеров.</span><span class="sxs-lookup"><span data-stu-id="c3368-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="c3368-197">**Службы центра Интернета вещей** будет построить и использовать в этом курсе, ссылается на **службы реестра контейнеров** для получения контейнеров для развертывания в устройство Edge.</span><span class="sxs-lookup"><span data-stu-id="c3368-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="c3368-198">Во-первых, выполните это [ссылку на портал Azure](https://portal.azure.com/)и войдите, используя свои учетные данные.</span><span class="sxs-lookup"><span data-stu-id="c3368-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="c3368-199">Перейдите к **создать ресурс** и найдите **реестр контейнеров**.</span><span class="sxs-lookup"><span data-stu-id="c3368-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![реестр контейнеров](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="c3368-201">Щелкните **создание**.</span><span class="sxs-lookup"><span data-stu-id="c3368-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="c3368-202">Настройте параметры службы:</span><span class="sxs-lookup"><span data-stu-id="c3368-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="c3368-203">Вставить имя проекта, в этом примере она называется **IoTCRegistry**.</span><span class="sxs-lookup"><span data-stu-id="c3368-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="c3368-204">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="c3368-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c3368-205">Для отслеживания, контроля доступа, подготовки и управлять, выставление счетов для коллекции активов Azure позволяет группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c3368-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="c3368-206">Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="c3368-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="c3368-207">Задайте расположение службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="c3368-208">Задайте **пользователя с правами администратора** для **включить**.</span><span class="sxs-lookup"><span data-stu-id="c3368-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="c3368-209">Задайте **SKU** для **основные**.</span><span class="sxs-lookup"><span data-stu-id="c3368-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="c3368-210">Нажмите кнопку **создать** и подождите создать службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="c3368-211">Когда появляется уведомление сообщающий об успешном создании *реестр контейнеров*, щелкните **перейти к ресурсу** перенаправление на страницу службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="c3368-212">В *реестр контейнеров* странице службы, щелкнув **ключи доступа**.</span><span class="sxs-lookup"><span data-stu-id="c3368-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="c3368-213">Запишите (можно использовать в блокноте) со следующими параметрами:</span><span class="sxs-lookup"><span data-stu-id="c3368-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="c3368-214">**Сервер входа**</span><span class="sxs-lookup"><span data-stu-id="c3368-214">**Login Server**</span></span>
    2. <span data-ttu-id="c3368-215">**Имя пользователя**</span><span class="sxs-lookup"><span data-stu-id="c3368-215">**Username**</span></span>
    3. <span data-ttu-id="c3368-216">**Пароль**</span><span class="sxs-lookup"><span data-stu-id="c3368-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="c3368-217">Глава 3 - центр Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="c3368-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="c3368-218">Теперь рассмотрим создание и настройка вашей **службы центра Интернета вещей**.</span><span class="sxs-lookup"><span data-stu-id="c3368-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="c3368-219">Если еще не выполнил вход, вход в [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c3368-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="c3368-220">После входа в систему, щелкните **создать ресурс** в левом верхнем углу, а поиск **центра Интернета вещей**и нажмите кнопку **ввод**.</span><span class="sxs-lookup"><span data-stu-id="c3368-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![Поиск учетной записи хранения](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="c3368-222">Новая страница будет предоставить описание **учетной записи хранения** службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="c3368-223">В нижней левой части этого запроса, нажмите кнопку **создать** кнопку, чтобы создать экземпляр этого службу.</span><span class="sxs-lookup"><span data-stu-id="c3368-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="c3368-225">Когда вы перейдете на **создать**, будут отображаться панели:</span><span class="sxs-lookup"><span data-stu-id="c3368-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="c3368-226">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="c3368-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c3368-227">Группа ресурсов предоставляет способ отслеживания, контроля доступа, Подготовка и управление выставлением счетов для набора средств Azure.</span><span class="sxs-lookup"><span data-stu-id="c3368-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c3368-228">Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="c3368-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="c3368-229">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылку на управление группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c3368-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="c3368-230">Выберите соответствующее **расположение** (используйте то же расположение во всех службах, создаваемых в этом курсе).</span><span class="sxs-lookup"><span data-stu-id="c3368-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="c3368-231">Вставить нужный **имя** для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="c3368-232">В нижней части страницы щелкните **далее: Размер и масштаб**.</span><span class="sxs-lookup"><span data-stu-id="c3368-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="c3368-234">На этой странице выберите ваш **цены и масштабирование уровня** (если это ваш первый экземпляр службы центра Интернета вещей, уровень "бесплатный" должна быть доступна для вас).</span><span class="sxs-lookup"><span data-stu-id="c3368-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="c3368-235">Щелкните **Просмотр и создание**.</span><span class="sxs-lookup"><span data-stu-id="c3368-235">Click on **Review + Create**.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="c3368-237">Просмотрите параметры и нажмите кнопку **создать**.</span><span class="sxs-lookup"><span data-stu-id="c3368-237">Review your settings and click on **Create**.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="c3368-239">После уведомления всплывает сообщающий об успешном создании *центра Интернета вещей* службы, щелкните **перейти к ресурсу** перенаправление на страницу службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="c3368-241">Прокрутите содержимое боковой панели в левой части до *автоматическое управление устройствами*, щелкните на **IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="c3368-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="c3368-243">В окне справа щелкните **добавить устройство IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="c3368-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="c3368-244">Колонка будет отображаться справа.</span><span class="sxs-lookup"><span data-stu-id="c3368-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="c3368-245">В колонке укажите новое устройство **идентификатор устройства** (имя по своему усмотрению).</span><span class="sxs-lookup"><span data-stu-id="c3368-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="c3368-246">Щелкните **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="c3368-246">Then, click **Save**.</span></span> <span data-ttu-id="c3368-247">*Основной* и *вторичные ключи* будет автоматически создавать, если у вас есть **автоматическое создание** отмечен.</span><span class="sxs-lookup"><span data-stu-id="c3368-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="c3368-249">Произойдет переход к *пограничные устройства Интернета вещей* раздел, где будут перечислены новое устройство.</span><span class="sxs-lookup"><span data-stu-id="c3368-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="c3368-250">Щелкните на новом устройстве (выделено красным цветом на изображении ниже).</span><span class="sxs-lookup"><span data-stu-id="c3368-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="c3368-252">На *сведений об устройстве* страницы, которая отображается, сделайте копию **строку подключения** (первичный ключ).</span><span class="sxs-lookup"><span data-stu-id="c3368-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="c3368-254">Вернитесь на панель слева и нажмите кнопку *политики общего доступа*, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="c3368-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="c3368-255">На открывшейся странице щелкните **iothubowner**, и колонка будет отображаться в правой части экрана.</span><span class="sxs-lookup"><span data-stu-id="c3368-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="c3368-256">Запишите (в «Блокнот») **строку подключения** (первичный ключ), для последующего использования при задании *строку подключения* к устройству.</span><span class="sxs-lookup"><span data-stu-id="c3368-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="c3368-258">Глава 4 - Настройка среды разработки</span><span class="sxs-lookup"><span data-stu-id="c3368-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="c3368-259">Для создания и развертывания модулей для *концентратора IoT Edge*, потребуются следующие компоненты, установленные на компьютере разработки под управлением Windows 10:</span><span class="sxs-lookup"><span data-stu-id="c3368-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="c3368-260">[Docker для Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), он запрашивает, следует создать учетную запись, чтобы иметь возможность загрузить.</span><span class="sxs-lookup"><span data-stu-id="c3368-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="c3368-261">[![скачать docker для windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="c3368-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c3368-262">Требуется docker *Windows 10 PRO*, *Enterprise 14393*, или *Windows Server 2016 RTM*, для запуска.</span><span class="sxs-lookup"><span data-stu-id="c3368-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="c3368-263">Если вы используете другие версии Windows 10, установку можно произвести с помощью Docker [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span><span class="sxs-lookup"><span data-stu-id="c3368-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="c3368-264">[Python 3.6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="c3368-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="c3368-265">[![скачать python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="c3368-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="c3368-266">[Visual Studio Code (также называется VS Code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="c3368-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="c3368-267">[![скачать VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="c3368-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="c3368-268">После установки программного обеспечения, упомянутых выше, необходимо перезагрузить компьютер.</span><span class="sxs-lookup"><span data-stu-id="c3368-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="c3368-269">Глава 5 - Настройка среды Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c3368-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="c3368-270">Теперь можно перейти к настройке устройства **под управлением ОС Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="c3368-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="c3368-271">Выполните следующие действия, чтобы установить необходимое программное обеспечение для развертывания контейнеров на плате.</span><span class="sxs-lookup"><span data-stu-id="c3368-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3368-272">Всегда должны предваряться команд терминала с помощью **sudo** для запуска в качестве пользователя с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="c3368-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="c3368-273">Например:</span><span class="sxs-lookup"><span data-stu-id="c3368-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="c3368-274">Откройте **терминалов Ubuntu**и используйте следующую команду для установки **pip**:</span><span class="sxs-lookup"><span data-stu-id="c3368-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! УКАЗАНИЕ]<span data-ttu-id="c3368-275"> можно открыть \*терминалов* очень просто с помощью сочетания клавиш: *\*Ctrl + Alt + T*\*.</span><span class="sxs-lookup"><span data-stu-id="c3368-275"> You can open \*Terminal* very easily through using the keyboard shortcut: *\*Ctrl + Alt + T*\*.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="c3368-276">В этой главе, может появиться запрос, по *терминалов*, для разрешения использования хранилища на устройстве, так и для ввода **д/н** (Да или нет), тип **«y»** и нажмите клавишу **Ввод** ключ, чтобы принять.</span><span class="sxs-lookup"><span data-stu-id="c3368-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="c3368-277">После выполнения этой команды, используйте следующую команду для установки **curl**:</span><span class="sxs-lookup"><span data-stu-id="c3368-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="c3368-278">Один раз **pip** и **curl** будут установлены, используйте следующую команду для установки **среды выполнения IoT Edge**, это необходимо для развертывания и управления модулями на плате:</span><span class="sxs-lookup"><span data-stu-id="c3368-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

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

5. <span data-ttu-id="c3368-279">На этом этапе вам будет предложено открыть *файл конфигурации среды выполнения*, вставляемый **Device Connection String**, который вы взяли (в в блокноте), при создании **службы центра Интернета вещей**  ([на шаге 14, Глава 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="c3368-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="c3368-280">Выполните приведенную ниже строку в окне терминала, чтобы открыть этот файл:</span><span class="sxs-lookup"><span data-stu-id="c3368-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="c3368-281">**Config.yaml** файл будет отображается, вы сможете изменить:</span><span class="sxs-lookup"><span data-stu-id="c3368-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="c3368-282">При открытии файла, может быть несколько запутанным.</span><span class="sxs-lookup"><span data-stu-id="c3368-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="c3368-283">Можно в редактирования этого файла текста *терминалов* сам.</span><span class="sxs-lookup"><span data-stu-id="c3368-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="c3368-284">Клавиши со стрелками на клавиатуре для прокрутки вниз (необходимо будет выполнить прокрутку вниз немного способом), для доступа к строке, которая содержит»:</span><span class="sxs-lookup"><span data-stu-id="c3368-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="c3368-285">"**\<ДОБАВЬТЕ СТРОКУ ПОДКЛЮЧЕНИЯ УСТРОЙСТВА &GT;**«.</span><span class="sxs-lookup"><span data-stu-id="c3368-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="c3368-286">Замените строки, **включая скобки**, с помощью **Device Connection String** отмечали ранее.</span><span class="sxs-lookup"><span data-stu-id="c3368-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="c3368-287">С помощью строки подключения в месте, на клавиатуре нажмите клавишу **Ctrl + X** ключи для сохранения файла.</span><span class="sxs-lookup"><span data-stu-id="c3368-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="c3368-288">Вам будет предложено подтвердить, введя **Y**. Затем нажмите клавишу **ввод** ключ для подтверждения.</span><span class="sxs-lookup"><span data-stu-id="c3368-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="c3368-289">Вы вернетесь к обычному *терминалов*.</span><span class="sxs-lookup"><span data-stu-id="c3368-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="c3368-290">Как только эти команды все выполняются успешно, будет установлен **среды выполнения IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="c3368-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="c3368-291">После инициализации среды выполнения на свой собственный каждый раз при включении устройства запустится и будет расположен в фоновом режиме, Ожидание модули для развертывания из **службы центра Интернета вещей**.</span><span class="sxs-lookup"><span data-stu-id="c3368-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="c3368-292">Выполните следующую команду для инициализации *среды выполнения IoT Edge*:</span><span class="sxs-lookup"><span data-stu-id="c3368-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="c3368-293">При внесении изменений в yaml-файл или указанные действия по настройке, необходимо будет снова, запустите приведенную выше строку перезапуска в рамках *терминалов*.</span><span class="sxs-lookup"><span data-stu-id="c3368-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="c3368-294">Проверьте *среды выполнения IoT Edge* состояние, выполнив следующую команду.</span><span class="sxs-lookup"><span data-stu-id="c3368-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="c3368-295">Среда выполнения должен отображаться с состоянием **активный (запущено)** зеленым цветом.</span><span class="sxs-lookup"><span data-stu-id="c3368-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="c3368-296">Нажмите клавишу **Ctrl-C** ключей, чтобы закрыть страницу состояния.</span><span class="sxs-lookup"><span data-stu-id="c3368-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="c3368-297">Можно убедиться, что *среды выполнения IoT Edge* извлекает контейнеров правильно, введя следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c3368-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="c3368-298">Должен появиться список с контейнерами два (2).</span><span class="sxs-lookup"><span data-stu-id="c3368-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="c3368-299">Это значение по умолчанию модули, которые создаются автоматически службой центра Интернета вещей (edgeAgent и edgeHub).</span><span class="sxs-lookup"><span data-stu-id="c3368-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="c3368-300">После создания и развертывания собственных модулей, они будут отображаться в этом списке, под по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c3368-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="c3368-301">Глава 6 - Установка расширения</span><span class="sxs-lookup"><span data-stu-id="c3368-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3368-302">Далее несколько глав посвящены (6 – 9) должны быть выполнены на компьютере Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c3368-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="c3368-303">Откройте **VS Code**.</span><span class="sxs-lookup"><span data-stu-id="c3368-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="c3368-304">Щелкните **расширения** кнопки (квадрат) на левой панели из VS Code, чтобы открыть **панели расширений**.</span><span class="sxs-lookup"><span data-stu-id="c3368-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="c3368-305">Поиск Чтобы установить, следующие расширения (как показано на рисунке ниже).</span><span class="sxs-lookup"><span data-stu-id="c3368-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="c3368-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="c3368-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="c3368-307">Azure IoT Toolkit</span><span class="sxs-lookup"><span data-stu-id="c3368-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="c3368-308">Docker</span><span class="sxs-lookup"><span data-stu-id="c3368-308">Docker</span></span>   

    ![Создание контейнера](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="c3368-310">После установки расширения, закройте и снова откройте VS Code.</span><span class="sxs-lookup"><span data-stu-id="c3368-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="c3368-311">С помощью VS Code откройте еще раз, перейдите к **Вид > встроенный терминал**.</span><span class="sxs-lookup"><span data-stu-id="c3368-311">With VS Code open once more, navigate to **View > Integrated terminal**.</span></span>

6. <span data-ttu-id="c3368-312">Будет выполнена установка **Cookiecutter**.</span><span class="sxs-lookup"><span data-stu-id="c3368-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="c3368-313">В окне терминала выполните следующую команду bash:</span><span class="sxs-lookup"><span data-stu-id="c3368-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! УКАЗАНИЕ]<span data-ttu-id="c3368-314"> при наличии проблем с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="c3368-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="c3368-315">Перезапустите VS Code и / или на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c3368-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="c3368-316">Может потребоваться переключиться **терминал VS Code** на тот, который вы использовали для установки Python, т. е. **Powershell** (особенно если на компьютере уже установлена среда Python).</span><span class="sxs-lookup"><span data-stu-id="c3368-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="c3368-317">В окне терминала вы найдете в раскрывающемся меню в правой части терминала.</span><span class="sxs-lookup"><span data-stu-id="c3368-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="c3368-318">![Создание контейнера](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="c3368-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="c3368-319">Убедитесь, что **Python** путь установки добавляется как **переменной среды** на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="c3368-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="c3368-320">Cookiecutter должны входить в один и тот же путь расположения.</span><span class="sxs-lookup"><span data-stu-id="c3368-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="c3368-321">Выполните инструкции из этого [ссылку на дополнительные сведения о переменных среды](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span><span class="sxs-lookup"><span data-stu-id="c3368-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="c3368-322">Один раз **Cookiecutter** закончил установку всех продуктов, то необходимо перезапустить компьютер, таким образом, чтобы **Cookiecutter** распознается как команду, в среде вашей системы.</span><span class="sxs-lookup"><span data-stu-id="c3368-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="c3368-323">Глава 7 - создание решения с контейнерами</span><span class="sxs-lookup"><span data-stu-id="c3368-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="c3368-324">На этом этапе необходимо создать контейнер, в модуле, помещаемых в *реестр контейнеров*.</span><span class="sxs-lookup"><span data-stu-id="c3368-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="c3368-325">После отправки контейнера, вы воспользуетесь *концентратора IoT Edge* службы для развертывания на устройстве, работающего в *среды выполнения IoT Edge*.</span><span class="sxs-lookup"><span data-stu-id="c3368-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="c3368-326">В VS Code щелкните **представление > палитру команд**.</span><span class="sxs-lookup"><span data-stu-id="c3368-326">From VS Code, click **View > Command palette**.</span></span>

2. <span data-ttu-id="c3368-327">В палитре, искать и запускать **Edge Интернета вещей Azure: Новое решение Iot Edge**.</span><span class="sxs-lookup"><span data-stu-id="c3368-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="c3368-328">Перейдите в расположение, где вы хотите создать решение.</span><span class="sxs-lookup"><span data-stu-id="c3368-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="c3368-329">Нажмите клавишу **ввод** ключ, чтобы принять расположение.</span><span class="sxs-lookup"><span data-stu-id="c3368-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="c3368-330">Присвойте имя для решения.</span><span class="sxs-lookup"><span data-stu-id="c3368-330">Give a name to your solution.</span></span> <span data-ttu-id="c3368-331">Нажмите клавишу **ввод** ключ, чтобы подтвердить ваш предоставленное имя.</span><span class="sxs-lookup"><span data-stu-id="c3368-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="c3368-332">Теперь вам будет предложено выбрать framework шаблона для вашего решения.</span><span class="sxs-lookup"><span data-stu-id="c3368-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="c3368-333">Нажмите кнопку **модуль Python**.</span><span class="sxs-lookup"><span data-stu-id="c3368-333">Click **Python Module**.</span></span> <span data-ttu-id="c3368-334">Нажмите клавишу **ввод** ключ, чтобы подтвердить этот выбор.</span><span class="sxs-lookup"><span data-stu-id="c3368-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="c3368-335">Присвойте имя для вашего модуля.</span><span class="sxs-lookup"><span data-stu-id="c3368-335">Give a name to your module.</span></span> <span data-ttu-id="c3368-336">Нажмите клавишу **ввод** ключ, чтобы подтвердить имя модуля.</span><span class="sxs-lookup"><span data-stu-id="c3368-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="c3368-337">Убедитесь, что внимание (с помощью «блокнота») и имя модуля, так как он используется в более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="c3368-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="c3368-338">Обратите внимание, предварительно созданные *репозиторий образов Docker* адрес будет отображаться в палитре.</span><span class="sxs-lookup"><span data-stu-id="c3368-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="c3368-339">Он имеет вид:</span><span class="sxs-lookup"><span data-stu-id="c3368-339">It will look like:</span></span>

    <span data-ttu-id="c3368-340">**localhost:5000 / имя МОДУЛЯ -**.</span><span class="sxs-lookup"><span data-stu-id="c3368-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="c3368-341">Удалить **localhost:5000**и в его место вставки *реестр контейнеров* **сервер входа** адрес, который вы записали при создании **контейнера Служба реестра** ([на шаге 8, Глава 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="c3368-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="c3368-342">Нажмите клавишу **ввод** ключ для проверки адреса.</span><span class="sxs-lookup"><span data-stu-id="c3368-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="c3368-343">На этом этапе создается решение, содержащее шаблон для вашего модуля Python и его структура будет отображаться в **изучение вкладку**, окна VS Code, в левой части экрана.</span><span class="sxs-lookup"><span data-stu-id="c3368-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="c3368-344">Если **изучение вкладку** является не открыто, его можно открыть, нажав кнопку верхнего уровня, на панели слева.</span><span class="sxs-lookup"><span data-stu-id="c3368-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Создание контейнера](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="c3368-346">Последний шаг для этой главы — щелкните и откройте **env-файле**, изнутри **изучение вкладку**и добавьте ваш *реестр контейнеров* **имяпользователя** и **пароль**.</span><span class="sxs-lookup"><span data-stu-id="c3368-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="c3368-347">Этот файл игнорируется git, но на создание приложений контейнера, будет задать учетные данные для доступа к **службы реестра контейнеров**.</span><span class="sxs-lookup"><span data-stu-id="c3368-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Создание контейнера](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="c3368-349">Глава 8 - изменения решения с контейнерами</span><span class="sxs-lookup"><span data-stu-id="c3368-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="c3368-350">Теперь завершим решение контейнера, обновив следующие файлы:</span><span class="sxs-lookup"><span data-stu-id="c3368-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="c3368-351">*основной<span></span>.py* скрипт python.</span><span class="sxs-lookup"><span data-stu-id="c3368-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="c3368-352">*файл Requirements.txt*.</span><span class="sxs-lookup"><span data-stu-id="c3368-352">*requirements.txt*.</span></span>
- <span data-ttu-id="c3368-353">*Deployment.Template.JSON*.</span><span class="sxs-lookup"><span data-stu-id="c3368-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="c3368-354">*Dockerfile.AMD64*</span><span class="sxs-lookup"><span data-stu-id="c3368-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="c3368-355">После этого создается *образы* папку, используемую скрипт python для проверки изображений, будет сравниваться с вашей *Custom Vision модели*.</span><span class="sxs-lookup"><span data-stu-id="c3368-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="c3368-356">Наконец, вы добавите *labels.txt* файл, чтобы облегчить чтение модели и *model.pb* файл, который является модель.</span><span class="sxs-lookup"><span data-stu-id="c3368-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="c3368-357">С помощью VS Code откройте, перейдите к папке модуля и найдите скрипт с именем **основной<span></span>.py**.</span><span class="sxs-lookup"><span data-stu-id="c3368-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="c3368-358">Дважды щелкните, чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="c3368-358">Double-click to open it.</span></span>

2. <span data-ttu-id="c3368-359">Удалите содержимое файла и вставьте следующий код:</span><span class="sxs-lookup"><span data-stu-id="c3368-359">Delete the content of the file and insert the following code:</span></span>

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

3.  <span data-ttu-id="c3368-360">Откройте файл с именем **requirements.txt**и замените его содержимое следующим:</span><span class="sxs-lookup"><span data-stu-id="c3368-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="c3368-361">Откройте файл с именем **deployment.template.json**и замените его следующее содержимое ниже рекомендации:</span><span class="sxs-lookup"><span data-stu-id="c3368-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="c3368-362">Поскольку будет иметь свои собственные, уникальным, структура JSON, необходимо будет вручную изменить (вместо того, чтобы скопировать пример).</span><span class="sxs-lookup"><span data-stu-id="c3368-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="c3368-363">Чтобы облегчить этот процесс, используйте под изображением в качестве руководства.</span><span class="sxs-lookup"><span data-stu-id="c3368-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="c3368-364">Области, будет выглядеть иначе к вам, но какие **не следует изменять, выделяется желтым цветом**.</span><span class="sxs-lookup"><span data-stu-id="c3368-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="c3368-365">**Разделы, которые необходимо удалить, — это выделенный красным значком.**</span><span class="sxs-lookup"><span data-stu-id="c3368-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="c3368-366">Не забудьте удалить правильный квадратные скобки, а также удалять запятые.</span><span class="sxs-lookup"><span data-stu-id="c3368-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Создание контейнера](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="c3368-368">Завершенные JSON должен выглядеть приблизительно так: (менее, с вашей уникальных различий: *ссылки на имя пользователя/пароль/модуль имя или модуля*):</span><span class="sxs-lookup"><span data-stu-id="c3368-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Создание контейнера](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="c3368-370">Откройте файл с именем **Dockerfile.amd64**и замените его содержимое следующим:</span><span class="sxs-lookup"><span data-stu-id="c3368-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

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

6.  <span data-ttu-id="c3368-371">Щелкните правой кнопкой мыши по папке **модули** (он будет иметь имя, указанное ранее; в далее в примере работу, он называется *pythonmodule*) и щелкните **новую папку**.</span><span class="sxs-lookup"><span data-stu-id="c3368-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="c3368-372">Назовите папку **образы**.</span><span class="sxs-lookup"><span data-stu-id="c3368-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="c3368-373">В папке добавьте некоторые образы, содержащие мыши или клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="c3368-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="c3368-374">Это будет изображения, которые будут проанализированы с помощью модели Tensorflow.</span><span class="sxs-lookup"><span data-stu-id="c3368-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="c3368-375">Если вы используете собственную модель, необходимо будет изменить его в соответствии с собственными данными модели.</span><span class="sxs-lookup"><span data-stu-id="c3368-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="c3368-376">Теперь необходимо будет получить **labels.txt** и **model.pb** файлы из папки модели, предыдущие загруженный (или созданы из собственных **пользовательская служба визуального распознавания** ), в [главе 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="c3368-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="c3368-377">Когда файлы, поместите их в решении, вместе с другими файлами.</span><span class="sxs-lookup"><span data-stu-id="c3368-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="c3368-378">Окончательный результат должен выглядеть как на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="c3368-378">The final result should look like the image below:</span></span>

    ![Создание контейнера](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="c3368-380">Глава 9 - пакет решения как контейнеры</span><span class="sxs-lookup"><span data-stu-id="c3368-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="c3368-381">Теперь вы готовы «упаковка» файлов в качестве контейнера и передать их в вашей **реестр контейнеров Azure**.</span><span class="sxs-lookup"><span data-stu-id="c3368-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="c3368-382">В VS Code откройте *интегрированный терминал* (**представление > встроенный терминал / CTRL + "**) и используйте следующую строку для входа с использованием **Docker** (замените значения команду с учетными данными вашей **реестр контейнеров Azure (ACR)**):</span><span class="sxs-lookup"><span data-stu-id="c3368-382">Within VS Code, open the *Integrated Terminal* (**View > Integrated Terminal / CTRL + \`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="c3368-383">Щелкните правой кнопкой мыши на файле **deployment.template.json**и нажмите кнопку **построить решение IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="c3368-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="c3368-384">Этот процесс сборки занимает некоторое время (в зависимости от устройства), поэтому будьте готовы подождать.</span><span class="sxs-lookup"><span data-stu-id="c3368-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="c3368-385">После завершения процесса построения, **deployment.json** файла должны быть созданы в новую папку с именем **config**.</span><span class="sxs-lookup"><span data-stu-id="c3368-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![Создание развертывания](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="c3368-387">Откройте **палитру команд** еще раз и выполните поиск **Azure: Войдите в**.</span><span class="sxs-lookup"><span data-stu-id="c3368-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="c3368-388">Следуйте инструкциям на экране, используя свои учетные данные учетной записи Azure; VS Code предоставит вам возможность *копирование и открытие*, которая скопирует кода устройства скоро потребуется и откройте веб-браузере по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c3368-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="c3368-389">Когда запрос, вставьте код устройства, для проверки подлинности компьютера.</span><span class="sxs-lookup"><span data-stu-id="c3368-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![копирование и открытие](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="c3368-391">Один раз со знаком в можно заметить, в нижней части *Проводник* панели новый раздел с именем **устройства центра Интернета вещей Azure**.</span><span class="sxs-lookup"><span data-stu-id="c3368-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="c3368-392">Щелкните здесь, чтобы развернуть его.</span><span class="sxs-lookup"><span data-stu-id="c3368-392">Click this section to expand it.</span></span>

    ![устройство Edge](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="c3368-394">Если устройство здесь нет, необходимо будет щелкнуть правой кнопкой мыши *устройства центра Интернета вещей Azure*, а затем нажмите кнопку **задать строку подключения центра Интернета вещей**.</span><span class="sxs-lookup"><span data-stu-id="c3368-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="c3368-395">Вы увидите, **палитру команд** (в верхней части VS Code), будет предлагать ввести ваш *строку подключения*.</span><span class="sxs-lookup"><span data-stu-id="c3368-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="c3368-396">Это *строку подключения* вы записали в конце [Глава 3](#chapter-3---the-iot-hub-service).</span><span class="sxs-lookup"><span data-stu-id="c3368-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="c3368-397">Нажмите клавишу **ввод** ключа, после копирования строки в.</span><span class="sxs-lookup"><span data-stu-id="c3368-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="c3368-398">Устройство должно загружаются и отображаются.</span><span class="sxs-lookup"><span data-stu-id="c3368-398">Your device should load, and appear.</span></span> <span data-ttu-id="c3368-399">Щелкните правой кнопкой мыши имя устройства, а затем нажмите кнопку **Создание развертывания для одного устройства**.</span><span class="sxs-lookup"><span data-stu-id="c3368-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![Создание развертывания](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="c3368-401">Вы получите *проводнике* строки, где вы можете перейти к **config** папку, а затем выберите **deployment.json** файла.</span><span class="sxs-lookup"><span data-stu-id="c3368-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="c3368-402">С помощью этого файла, выбранного, щелкните **выбрать Edge манифест развертывания** кнопки.</span><span class="sxs-lookup"><span data-stu-id="c3368-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![Создание развертывания](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="c3368-404">На этом этапе вы предоставили вашей **службы центра Интернета вещей** с манифестом для него для развертывания контейнера, как модуль, из вашего **реестр контейнеров Azure**, эффективно развернуть его в устройстве.</span><span class="sxs-lookup"><span data-stu-id="c3368-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="c3368-405">Чтобы просмотреть сообщения, отправляемые с устройства в центр Интернета вещей, снова щелкните правой кнопкой мыши имя устройства в **устройства центра Интернета вещей Azure** раздела **Explorer** панели и щелкните **начать наблюдение Сообщения D2C**.</span><span class="sxs-lookup"><span data-stu-id="c3368-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="c3368-406">Сообщения, отправляемые с устройства должны появиться в окне терминала VS.</span><span class="sxs-lookup"><span data-stu-id="c3368-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="c3368-407">Сохраняйте Терпение, так как это может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="c3368-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="c3368-408">См. в разделе Далее отладки и проверки, если развертывание прошло успешно.</span><span class="sxs-lookup"><span data-stu-id="c3368-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="c3368-409">Этот модуль теперь будет повторяться, между ними в **образы** папки и анализировать их, с каждой итерацией.</span><span class="sxs-lookup"><span data-stu-id="c3368-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="c3368-410">Это очевидно, что просто показывает, как получить основные машинного обучения модели для работы в среде устройств IoT Edge.</span><span class="sxs-lookup"><span data-stu-id="c3368-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="c3368-411">Чтобы расширить функциональные возможности в этом примере, можно продолжить несколькими способами.</span><span class="sxs-lookup"><span data-stu-id="c3368-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="c3368-412">Один из способов может быть включая некоторый код в контейнере, который фиксирует фотографий с веб-камера, подключенная к устройству, сохраняет изображения в папке images.</span><span class="sxs-lookup"><span data-stu-id="c3368-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="c3368-413">Еще одним способом можете скопировать изображений из устройства в контейнер.</span><span class="sxs-lookup"><span data-stu-id="c3368-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="c3368-414">Является удобным способом для этого выполните следующую команду на устройстве Интернета вещей терминалов (возможно небольшое приложение может выполнять задания, если вы хотели бы автоматизировать процесс).</span><span class="sxs-lookup"><span data-stu-id="c3368-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="c3368-415">Эта команда можно проверить, запустив его вручную из папки, где хранятся файлы:</span><span class="sxs-lookup"><span data-stu-id="c3368-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="c3368-416">Глава 10 - отладки в среду выполнения IoT Edge</span><span class="sxs-lookup"><span data-stu-id="c3368-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="c3368-417">Ниже приведены список командные строки и советы, которые помогут отслеживать и отлаживать действия обмена сообщениями из *среды выполнения IoT Edge*, из вашего **устройство Ubuntu**.</span><span class="sxs-lookup"><span data-stu-id="c3368-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="c3368-418">Проверьте *среды выполнения IoT Edge* состояние, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c3368-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="c3368-419">Не забудьте нажать **Ctrl + C**, чтобы завершить, просмотрите ее состояние.</span><span class="sxs-lookup"><span data-stu-id="c3368-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="c3368-420">Список контейнеров, развернутых в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="c3368-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="c3368-421">Если *службы центра Интернета вещей* развернул контейнеры успешно, они будут отображаться, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c3368-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="c3368-422">или</span><span class="sxs-lookup"><span data-stu-id="c3368-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="c3368-423">Выше показан хороший способ проверить ли модуль успешно развернуто, так как он будет отображаться в списке; в противном случае будет **только** см. в разделе *edgeHub* и *edgeAgent*.</span><span class="sxs-lookup"><span data-stu-id="c3368-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="c3368-424">Чтобы отобразить код журналы контейнера, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c3368-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="c3368-425">**Полезные команды для управления в среду выполнения Edge Интернета вещей:**</span><span class="sxs-lookup"><span data-stu-id="c3368-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="c3368-426">Чтобы удалить все контейнеры на узле:</span><span class="sxs-lookup"><span data-stu-id="c3368-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="c3368-427">Чтобы остановить *среды выполнения IoT Edge*:</span><span class="sxs-lookup"><span data-stu-id="c3368-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="c3368-428">Глава 11. Создание службы таблиц</span><span class="sxs-lookup"><span data-stu-id="c3368-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="c3368-429">Перейдите назад на портал Azure, которой будет создаваться в службу таблиц Azure, создав ресурс хранилища.</span><span class="sxs-lookup"><span data-stu-id="c3368-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="c3368-430">Если еще не выполнил вход, вход в [портал Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c3368-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="c3368-431">После входа в систему, щелкните **создать ресурс**в левом верхнем углу, а поиск **учетной записи хранения**и нажмите клавишу **ввод** ключ, следует начать поиск.</span><span class="sxs-lookup"><span data-stu-id="c3368-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="c3368-432">После ее значок появился, нажмите кнопку **учетная запись хранения — большой двоичный объект, файл, таблица, очередь** из списка.</span><span class="sxs-lookup"><span data-stu-id="c3368-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Поиск учетной записи хранения](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="c3368-434">Новая страница будет предоставить описание **учетной записи хранения** службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="c3368-435">В нижней левой части этого запроса, нажмите кнопку **создать** кнопку, чтобы создать экземпляр этого службу.</span><span class="sxs-lookup"><span data-stu-id="c3368-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Создание экземпляра хранилища](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="c3368-437">Когда вы перейдете на **создать**, будут отображаться панели:</span><span class="sxs-lookup"><span data-stu-id="c3368-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="c3368-438">Вставить нужный **имя** для данного экземпляра службы (*должны указываться прописными буквами*).</span><span class="sxs-lookup"><span data-stu-id="c3368-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="c3368-439">Для **модели развертывания**, нажмите кнопку **Resource manager**.</span><span class="sxs-lookup"><span data-stu-id="c3368-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="c3368-440">Для **тип учетной записи**, с помощью раскрывающегося списка, щелкните **хранилища (общего назначения версии 1)**.</span><span class="sxs-lookup"><span data-stu-id="c3368-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="c3368-441">Щелкните соответствующий **расположение**.</span><span class="sxs-lookup"><span data-stu-id="c3368-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="c3368-442">Для **репликации** в раскрывающемся меню щелкните **Read-access геоизбыточного хранилища (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="c3368-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="c3368-443">Для **производительности**, нажмите кнопку **стандартный**.</span><span class="sxs-lookup"><span data-stu-id="c3368-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="c3368-444">В рамках **требуется безопасное перемещение** щелкните **отключено**.</span><span class="sxs-lookup"><span data-stu-id="c3368-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="c3368-445">Из **подписки** в раскрывающемся меню выберите соответствующую подписку.</span><span class="sxs-lookup"><span data-stu-id="c3368-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="c3368-446">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="c3368-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c3368-447">Для отслеживания, контроля доступа, подготовки и управлять, выставление счетов для коллекции активов Azure позволяет группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c3368-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="c3368-448">Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="c3368-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="c3368-449">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылку на управление группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c3368-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="c3368-450">Оставьте **виртуальные сети** как **отключено**, если этот вариант для вас.</span><span class="sxs-lookup"><span data-stu-id="c3368-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="c3368-451">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="c3368-451">Click **Create**.</span></span>

        ![Заполните сведения о хранилище](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="c3368-453">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="c3368-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="c3368-454">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="c3368-455">Щелкните уведомлений для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-455">Click on the notifications to explore your new Service instance.</span></span>

    ![новое уведомление хранилища](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="c3368-457">Нажмите кнопку **перейти к ресурсу** кнопки в уведомления, а также будут выполнены на новую страницу Общие сведения о службе хранилища экземпляра.</span><span class="sxs-lookup"><span data-stu-id="c3368-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![Перейти к ресурсу](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="c3368-459">На странице обзора, в правой части окна щелкните **таблиц**.</span><span class="sxs-lookup"><span data-stu-id="c3368-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![Таблицы](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="c3368-461">На правой панели появятся **службы таблиц** сведения, в которой необходимо добавить новую таблицу.</span><span class="sxs-lookup"><span data-stu-id="c3368-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="c3368-462">Это можно сделать, щелкнув **+ таблицы** кнопку в левом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="c3368-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![Открытие таблиц](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="c3368-464">Новая страница отображается, при котором необходимо ввести **имя таблицы**.</span><span class="sxs-lookup"><span data-stu-id="c3368-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="c3368-465">Это имя, которое будет использовать для обращения к данным в приложении в последующих главах (Создание приложения-функции и Power BI).</span><span class="sxs-lookup"><span data-stu-id="c3368-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="c3368-466">Вставить **IoTMessages** как имя (вы можете выбрать собственные, просто запомните его при использовании этого документа) и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="c3368-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="c3368-467">После создания новой таблицы, можно будет увидеть в **службы таблиц** страницы (внизу).</span><span class="sxs-lookup"><span data-stu-id="c3368-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![создать новую таблицу](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="c3368-469">Теперь щелкните **ключи доступа** и сделайте копию **имя учетной записи хранения** и **ключ** (с помощью вашей Блокнот), эти значения понадобятся позже в этом курсе, при создании **Приложения-функции azure**.</span><span class="sxs-lookup"><span data-stu-id="c3368-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![создать новую таблицу](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="c3368-471">С помощью панели слева, прокрутите до *службы таблиц* раздела и нажмите кнопку **таблиц** (или **обзор таблиц**, на более новые порталах) и сделайте копию  **URL-адрес таблицы** (с помощью вашей блокнота).</span><span class="sxs-lookup"><span data-stu-id="c3368-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="c3368-472">Это значение будет использовать позже в этом курсе, при связывании таблицы вашей **Power BI** приложения.</span><span class="sxs-lookup"><span data-stu-id="c3368-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![создать новую таблицу](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="c3368-474">Глава 12 - завершение таблицы Azure</span><span class="sxs-lookup"><span data-stu-id="c3368-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="c3368-475">Теперь, когда ваш **службы таблиц** учетной записи хранения установлен и настроен, пришло время для добавления данных, который будет использоваться для хранения и извлечения данных.</span><span class="sxs-lookup"><span data-stu-id="c3368-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="c3368-476">Редактирование таблиц можно сделать с помощью **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c3368-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="c3368-477">Откройте **Visual Studio** (**не** Visual Studio Code).</span><span class="sxs-lookup"><span data-stu-id="c3368-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="c3368-478">В меню **представление > Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="c3368-478">From the menu, click **View > Cloud Explorer**.</span></span>

    ![Откройте cloud explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="c3368-480">**Cloud Explorer** будут открываться как закрепленного элемента (быть пациента, так как загрузка может занять время).</span><span class="sxs-lookup"><span data-stu-id="c3368-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="c3368-481">Если подписка использовалась для создания вашего *учетные записи хранения* не отображается, убедитесь, что у вас есть:</span><span class="sxs-lookup"><span data-stu-id="c3368-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="c3368-482">Вход в ту же учетную запись, которая использовалась для портала Azure.</span><span class="sxs-lookup"><span data-stu-id="c3368-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="c3368-483">Выбранные подписки на странице управления учетными записями (может потребоваться применить фильтр из параметров учетной записи):</span><span class="sxs-lookup"><span data-stu-id="c3368-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![найти подписку](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="c3368-485">Будут показаны облачных служб Azure.</span><span class="sxs-lookup"><span data-stu-id="c3368-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="c3368-486">Найти **учетные записи хранения** и щелкните стрелку влево, чтобы развернуть учетные записи.</span><span class="sxs-lookup"><span data-stu-id="c3368-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Откройте учетные записи хранения](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="c3368-488">После развернут, только что созданный **учетной записи хранения** должны быть доступны.</span><span class="sxs-lookup"><span data-stu-id="c3368-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="c3368-489">Щелкните стрелку слева от хранилища и найдите после, развернута, **таблиц** и щелкните стрелку рядом с ним, чтобы отобразить **таблицы** созданный в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="c3368-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="c3368-490">Дважды щелкните ваш **таблицы**.</span><span class="sxs-lookup"><span data-stu-id="c3368-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="c3368-491">Таблица откроется в центре окна Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3368-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="c3368-492">Щелкните значок таблицы с **+** (плюс) на нем.</span><span class="sxs-lookup"><span data-stu-id="c3368-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![Добавление новой таблицы](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="c3368-494">Откроется окно с запроса позволяет *Добавление сущности*.</span><span class="sxs-lookup"><span data-stu-id="c3368-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="c3368-495">Вы создадите только одну сущность, на то, что он будет иметь три свойства.</span><span class="sxs-lookup"><span data-stu-id="c3368-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="c3368-496">Можно будет заметить, что *PartitionKey* и *RowKey* уже предоставляются, так как они используются в таблице для поиска данных.</span><span class="sxs-lookup"><span data-stu-id="c3368-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![ключ раздела и строки](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="c3368-498">Обновите следующие значения:</span><span class="sxs-lookup"><span data-stu-id="c3368-498">Update the following values:</span></span>

    - <span data-ttu-id="c3368-499">Имя: **PartitionKey**, значение: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="c3368-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="c3368-500">Имя: **RowKey**, значение: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="c3368-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="c3368-501">Щелкните **добавить свойство** (в левом нижнем углу *Добавление сущности* окна) и добавьте следующее свойство:</span><span class="sxs-lookup"><span data-stu-id="c3368-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="c3368-502">**Содержимое MessageContent**, как *строка*, оставьте значение пустым.</span><span class="sxs-lookup"><span data-stu-id="c3368-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="c3368-503">Таблица должна совпадать с той, на рисунке ниже:</span><span class="sxs-lookup"><span data-stu-id="c3368-503">Your table should match the one in the image below:</span></span>

    ![добавить правильные значения](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="c3368-505">Почему сущность имеет номер 1 в ключ строки, так как может потребоваться добавить дополнительные сообщения, следует желании поэкспериментировать с помощью этого курса.</span><span class="sxs-lookup"><span data-stu-id="c3368-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="c3368-506">Нажмите кнопку **ОК** при завершении работы.</span><span class="sxs-lookup"><span data-stu-id="c3368-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="c3368-507">Таблица теперь готов для использования.</span><span class="sxs-lookup"><span data-stu-id="c3368-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="c3368-508">Глава 13 - Создание приложения-функции Azure</span><span class="sxs-lookup"><span data-stu-id="c3368-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="c3368-509">Пришло время теперь для создания *приложение-функцию Azure*, которого будет вызываться *службы центра Интернета вещей* для хранения *IoT Edge* устройства сообщений в **таблицы** Служба, которая была создана в предыдущей главе.</span><span class="sxs-lookup"><span data-stu-id="c3368-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="c3368-510">Во-первых необходимо создать файл, который позволит загружать библиотеки, необходимые функции Azure.</span><span class="sxs-lookup"><span data-stu-id="c3368-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="c3368-511">Откройте **Блокнот** (нажмите клавишу *ключ Windows*и тип *Блокнот*).</span><span class="sxs-lookup"><span data-stu-id="c3368-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![Откройте в блокноте](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="c3368-513">Откройте Блокнот вставьте в него приведенную ниже структуру JSON.</span><span class="sxs-lookup"><span data-stu-id="c3368-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="c3368-514">Как только вы это сделали, сохраните его на рабочем столе как **project.json**.</span><span class="sxs-lookup"><span data-stu-id="c3368-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="c3368-515">Этот файл определяет библиотеки, которые будет использовать функции.</span><span class="sxs-lookup"><span data-stu-id="c3368-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="c3368-516">При использовании NuGet, будут вам знакомы.</span><span class="sxs-lookup"><span data-stu-id="c3368-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="c3368-517">Очень важно, что система именования является верным; обеспечить его **нет .txt** расширение файла.</span><span class="sxs-lookup"><span data-stu-id="c3368-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="c3368-518">Ниже приведены ссылки.</span><span class="sxs-lookup"><span data-stu-id="c3368-518">See below for reference:</span></span>
    >
    > ![JSON, сохранение](images/AzureLabs-Lab313-52.png)

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

3.  <span data-ttu-id="c3368-520">Войдите в [портала Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c3368-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="c3368-521">После входа в систему щелкните **создать ресурс** в левом верхнем углу, а поиск **приложения-функции**и нажмите клавишу **ввод** искомый ключ.</span><span class="sxs-lookup"><span data-stu-id="c3368-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="c3368-522">Нажмите кнопку *приложения-функции* из результатов, чтобы открыть новую область.</span><span class="sxs-lookup"><span data-stu-id="c3368-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![Поиск приложения-функции](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="c3368-524">Новая панель предоставляет описание **приложения-функции** службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="c3368-525">В левом нижнем этой панели, щелкните **создать** кнопку, чтобы создать ассоциацию с данным службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![экземпляре приложения-функции](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="c3368-527">Когда вы перейдете на **создать**, задайте приведенные ниже:</span><span class="sxs-lookup"><span data-stu-id="c3368-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="c3368-528">Для **имя_приложения**, вставить желаемого имени для данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="c3368-529">Выберите **подписки**.</span><span class="sxs-lookup"><span data-stu-id="c3368-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="c3368-530">Выберите ценовую категорию, соответствующие, если это первое время создания **функция службы приложений**, уровень "бесплатный" должны быть доступны для вас.</span><span class="sxs-lookup"><span data-stu-id="c3368-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="c3368-531">Выберите **группы ресурсов** или создайте новую.</span><span class="sxs-lookup"><span data-stu-id="c3368-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c3368-532">Для отслеживания, контроля доступа, подготовки и управлять, выставление счетов для коллекции активов Azure позволяет группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c3368-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="c3368-533">Рекомендуется держать все службы Azure, связанные с одного проекта (например, такие как этих курсов) для распространенных группы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="c3368-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="c3368-534">Если вы хотите получить дополнительные сведения о группах ресурсов Azure, выполните инструкции из этого [ссылку на управление группой ресурсов](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c3368-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="c3368-535">Для **ОС**, нажмите кнопку Windows, так как целевую платформу.</span><span class="sxs-lookup"><span data-stu-id="c3368-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="c3368-536">Выберите **текущему плану размещения и** (этот учебник использование **план потребления**.</span><span class="sxs-lookup"><span data-stu-id="c3368-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="c3368-537">Выберите **расположение** (выберите то же расположение, как хранилище, вы создали на предыдущем шаге)</span><span class="sxs-lookup"><span data-stu-id="c3368-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="c3368-538">Для **хранения** разделе **необходимо выбрать службу хранения, созданную на предыдущем шаге**.</span><span class="sxs-lookup"><span data-stu-id="c3368-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="c3368-539">Вам не потребуется *Application Insights* в этом приложении, поэтому вы можете оставить его **Off**.</span><span class="sxs-lookup"><span data-stu-id="c3368-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="c3368-540">Нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="c3368-540">Click **Create**.</span></span>

        ![Создайте новый экземпляр](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="c3368-542">Когда вы перейдете на **создать**, вы получите ожидания службы должен быть создан, это может занять около минуты.</span><span class="sxs-lookup"><span data-stu-id="c3368-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="c3368-543">Уведомление будет отображаться на портале, после создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![новое уведомление](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="c3368-545">Щелкните уведомление, после успешного развертывания (завершено).</span><span class="sxs-lookup"><span data-stu-id="c3368-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="c3368-546">Нажмите кнопку **перейти к ресурсу** кнопки в уведомлении для просмотра в новом экземпляре службы.</span><span class="sxs-lookup"><span data-stu-id="c3368-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Перейти к ресурсу](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="c3368-548">В левой части новой панели, щелкните **+** (плюс) значок рядом с полем *функции*, чтобы создать новую функцию.</span><span class="sxs-lookup"><span data-stu-id="c3368-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![Добавление новой функции](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="c3368-550">На центральной панели **функция** откроется окно создания.</span><span class="sxs-lookup"><span data-stu-id="c3368-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="c3368-551">Прокрутите дальше и щелкните **пользовательская функция**.</span><span class="sxs-lookup"><span data-stu-id="c3368-551">Scroll down further, and click on **Custom function**.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="c3368-553">Прокрутите страницу вниз, далее, пока не найдете **центра Интернета вещей (концентратора событий)**, затем щелкните его.</span><span class="sxs-lookup"><span data-stu-id="c3368-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="c3368-555">В **центра Интернета вещей (концентратора событий)** задать колонке **языка** для **C#** и выберите команду **новый**.</span><span class="sxs-lookup"><span data-stu-id="c3368-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="c3368-557">Убедитесь, что в окне, которое будет отображаться, **центра Интернета вещей** выбран и имя *центра Интернета вещей* соответствует поле с именем вашей *службы центра Интернета вещей* , у вас есть созданный ранее ([на шаге 8, Глава 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="c3368-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="c3368-558">Нажмите кнопку **выберите** кнопки.</span><span class="sxs-lookup"><span data-stu-id="c3368-558">Then click the **Select** button.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="c3368-560">Вернитесь на **центра Интернета вещей (концентратора событий)** щелкните **создать**.</span><span class="sxs-lookup"><span data-stu-id="c3368-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="c3368-562">Вы будете перенаправлены к редактору функции.</span><span class="sxs-lookup"><span data-stu-id="c3368-562">You will be redirected to the function editor.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="c3368-564">Удалите весь код в нем и замените его следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="c3368-564">Delete all the code in it and replace it with the following:</span></span>

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

19. <span data-ttu-id="c3368-565">Измените следующие переменные, таким образом, чтобы они соответствуют соответствующие значения (**таблицы** и **хранения** значения, из [шаг с 11 и 13, соответственно, глава 11](#chapter-11---create-table-service)), Вы найдете в вашей **учетной записи хранения**:</span><span class="sxs-lookup"><span data-stu-id="c3368-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="c3368-566">**tableName**, именем вашего **таблицы** в вашей **учетной записи хранения**.</span><span class="sxs-lookup"><span data-stu-id="c3368-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="c3368-567">**tableURL**, URL-адресом вашей **таблицы** в вашей **учетной записи хранения**.</span><span class="sxs-lookup"><span data-stu-id="c3368-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="c3368-568">**storageAccountName**, именем значение, соответствующее имя вашей **учетной записи хранения** имя.</span><span class="sxs-lookup"><span data-stu-id="c3368-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="c3368-569">**storageAccountKey**, с ключом, полученным в службе хранилища, созданный ранее.</span><span class="sxs-lookup"><span data-stu-id="c3368-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="c3368-571">С помощью кода в месте, нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="c3368-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="c3368-572">Затем щелкните **\<** значок (стрелка), в правой части страницы.</span><span class="sxs-lookup"><span data-stu-id="c3368-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="c3368-574">Панель будет слайд в справа.</span><span class="sxs-lookup"><span data-stu-id="c3368-574">A panel will slide in from the right.</span></span> <span data-ttu-id="c3368-575">В этой панели, щелкните **отправить**и *браузер файлов* будет отображаться.</span><span class="sxs-lookup"><span data-stu-id="c3368-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="c3368-576">Перейдите к и нажмите кнопку, **project.json** файл, который вы создали в **Блокнот** ранее и нажмите кнопку **откройте** кнопки.</span><span class="sxs-lookup"><span data-stu-id="c3368-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="c3368-577">Этот файл определяет библиотеки, на которые будет использовать функции.</span><span class="sxs-lookup"><span data-stu-id="c3368-577">This file defines the libraries that your function will use.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="c3368-579">Когда файл отправлен, он будет отображаться на панели справа.</span><span class="sxs-lookup"><span data-stu-id="c3368-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="c3368-580">Если щелкнуть его, откроется его в **функция** редактора.</span><span class="sxs-lookup"><span data-stu-id="c3368-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="c3368-581">Он должен выглядеть **точно** так же, как следующему изображению.</span><span class="sxs-lookup"><span data-stu-id="c3368-581">It must look **exactly** the same as the next image.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="c3368-583">На этом этапе было бы неплохо для тестирования возможности этой функции для сохранения сообщения на ваш *таблицы*.</span><span class="sxs-lookup"><span data-stu-id="c3368-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="c3368-584">В верхней правой части окна, щелкните **теста**.</span><span class="sxs-lookup"><span data-stu-id="c3368-584">On the top right side of the window, click on **Test**.</span></span>

    ![Пользовательская функция](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="c3368-586">Вставка сообщения в **текст запроса**, как показано в показанном выше рисунке и нажмите кнопку на **запуска**.</span><span class="sxs-lookup"><span data-stu-id="c3368-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="c3368-587">Функция будет выполняться, отображения состояния результата (появится зеленая **состояние 202 Accepted**выше *вывода* окно, которое означает, что он был успешно выполнен вызов):</span><span class="sxs-lookup"><span data-stu-id="c3368-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![Выходной результат](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="c3368-589">Глава 14 - представление активных сообщений</span><span class="sxs-lookup"><span data-stu-id="c3368-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="c3368-590">Если теперь открыть Visual Studio (**не** Visual Studio Code), вы можете визуализировать сообщения результатами теста, так как он будет храниться в *содержимое MessageContent* строка области.</span><span class="sxs-lookup"><span data-stu-id="c3368-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![Пользовательская функция](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="c3368-592">С помощью службы таблиц и приложения-функции на месте, Ubuntu сообщения устройства будет отображаться в вашей *IoTMessages* таблицы.</span><span class="sxs-lookup"><span data-stu-id="c3368-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="c3368-593">Если еще не работает, запустите устройства и вы сможете видны результат сообщения с устройства и модуль, в пределах таблицы, с помощью Visual Studio *Cloud Explorer*.</span><span class="sxs-lookup"><span data-stu-id="c3368-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![Визуализация данных](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="c3368-595">Глава 15 - установки Power BI</span><span class="sxs-lookup"><span data-stu-id="c3368-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="c3368-596">Для визуализации данных из устройства Интернета ВЕЩЕЙ, помогут вам настроить **Power BI** (версии), для сбора данных из *таблицы* службы, который вы только что создали.</span><span class="sxs-lookup"><span data-stu-id="c3368-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="c3368-597">*HoloLens* версию Power BI будет использовать эти данные для визуализации результат.</span><span class="sxs-lookup"><span data-stu-id="c3368-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="c3368-598">Откройте Microsoft Store в Windows 10 и выполните поиск **Power BI Desktop**.</span><span class="sxs-lookup"><span data-stu-id="c3368-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="c3368-600">Скачайте приложение.</span><span class="sxs-lookup"><span data-stu-id="c3368-600">Download the application.</span></span> <span data-ttu-id="c3368-601">После завершения загрузки, откройте его.</span><span class="sxs-lookup"><span data-stu-id="c3368-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="c3368-602">Войдите на *Power BI* с вашей **учетной записи Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="c3368-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="c3368-603">Вы может перенаправляться в браузере, чтобы зарегистрироваться.</span><span class="sxs-lookup"><span data-stu-id="c3368-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="c3368-604">После вы зарегистрировались, вернитесь в приложение Power BI и снова войти в систему.</span><span class="sxs-lookup"><span data-stu-id="c3368-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="c3368-605">Щелкните **получить данные** и выберите команду **более...** .</span><span class="sxs-lookup"><span data-stu-id="c3368-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="c3368-607">Нажмите кнопку **Azure**, **Azure Table Storage**, затем щелкните **Connect**.</span><span class="sxs-lookup"><span data-stu-id="c3368-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="c3368-609">Вам будет предложено вставить **URL-адрес таблицы** собранными ранее ([на шаге 13 Глава 11](#chapter-11---create-table-service)), при создании службы таблиц.</span><span class="sxs-lookup"><span data-stu-id="c3368-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="c3368-610">После вставки URL-адрес, удалите часть пути, относящаяся к таблице «вложенную папку», (который был IoTMessages, в этом курсе).</span><span class="sxs-lookup"><span data-stu-id="c3368-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="c3368-611">Окончательный результат должен быть, показанной на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="c3368-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="c3368-612">Нажмите кнопку на **ОК**.</span><span class="sxs-lookup"><span data-stu-id="c3368-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="c3368-614">Вам будет предложено вставить **ключ к хранилищу** , записанными ([на шаге 11 Глава 11](#chapter-11---create-table-service)) ранее при создании хранилище таблиц.</span><span class="sxs-lookup"><span data-stu-id="c3368-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="c3368-615">Нажмите кнопку на **Connect**.</span><span class="sxs-lookup"><span data-stu-id="c3368-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="c3368-617">Объект **панель "Navigator"** будет отображаться, установите флажок рядом с таблицы и щелкните **нагрузки**.</span><span class="sxs-lookup"><span data-stu-id="c3368-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="c3368-619">Таблица теперь загружена в Power BI, но он требует запрос для отображения значения в нем.</span><span class="sxs-lookup"><span data-stu-id="c3368-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="c3368-620">Чтобы сделать это, щелкните правой кнопкой мыши на имя таблицы, расположенных в **«поля»** в правой части экрана.</span><span class="sxs-lookup"><span data-stu-id="c3368-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="c3368-621">Нажмите кнопку на **изменить запрос**.</span><span class="sxs-lookup"><span data-stu-id="c3368-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="c3368-623">Объект **редактора Power Query** откроется в новом окне, отображение таблицы.</span><span class="sxs-lookup"><span data-stu-id="c3368-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="c3368-624">Щелкните слово **записи** в *содержимого* столбец таблицы, для визуализации хранимых содержимого.</span><span class="sxs-lookup"><span data-stu-id="c3368-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="c3368-626">Щелкните **в таблице**, в верхней левой части окна.</span><span class="sxs-lookup"><span data-stu-id="c3368-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="c3368-628">Щелкните **закрыть и применить**.</span><span class="sxs-lookup"><span data-stu-id="c3368-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="c3368-630">После завершения загрузки запроса, в **«поля»**, в правой части экрана, установите флажки рядом с соответствующими параметрами **имя** и **значение**, визуализация **содержимое MessageContent** содержимое столбца.</span><span class="sxs-lookup"><span data-stu-id="c3368-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="c3368-632">Щелкните **значок синей диска** в левой верхней части окна, чтобы сохранить результаты работы в папку по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="c3368-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="c3368-634">Теперь можно щелкнуть "Опубликовать" для передачи таблицы в рабочей области.</span><span class="sxs-lookup"><span data-stu-id="c3368-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="c3368-635">При появлении запроса, щелкните **Моя рабочая область** и нажмите кнопку *выберите*.</span><span class="sxs-lookup"><span data-stu-id="c3368-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="c3368-636">Подождите вывести результат успешной отправки.</span><span class="sxs-lookup"><span data-stu-id="c3368-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="c3368-639">Следующая глава — определенные HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3368-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="c3368-640">Power BI не является доступна в качестве иммерсивные приложения, однако запуском настольной версии на портале Windows смешанной реальности (также называемые со скалы дома), через классическое приложение.</span><span class="sxs-lookup"><span data-stu-id="c3368-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="c3368-641">Глава 16 - Power BI для отображения данных на HoloLens</span><span class="sxs-lookup"><span data-stu-id="c3368-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="c3368-642">На ваш HoloLens, войдите в **Microsoft Store**, можно просмотреть, выбрав его значок в списке приложений.</span><span class="sxs-lookup"><span data-stu-id="c3368-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="c3368-644">Найдите и загрузите **Power BI** приложения.</span><span class="sxs-lookup"><span data-stu-id="c3368-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="c3368-646">Запуск **Power BI** из списка приложений.</span><span class="sxs-lookup"><span data-stu-id="c3368-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="c3368-647">**Power BI** может потребоваться выполнить вход в ваш **учетной записи Microsoft 365**.</span><span class="sxs-lookup"><span data-stu-id="c3368-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="c3368-648">Один раз в приложении, в рабочей области должен отображаться по умолчанию как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="c3368-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="c3368-649">Если, не произойдет, просто щелкните значок рабочую область в левой части окна.</span><span class="sxs-lookup"><span data-stu-id="c3368-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="c3368-651">Ваш завершения приложения Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="c3368-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="c3368-652">Поздравляем, вы успешно создали службу центра Интернета вещей с имитацией устройства Edge виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="c3368-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="c3368-653">Устройства могут взаимодействовать результатов модели в службе таблиц Azure, с помощью приложения-функции Azure, который считывается в Power BI и визуализации в Microsoft HoloLens машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="c3368-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c3368-655">Упражнения премии</span><span class="sxs-lookup"><span data-stu-id="c3368-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c3368-656">Упражнение 1</span><span class="sxs-lookup"><span data-stu-id="c3368-656">Exercise 1</span></span>

<span data-ttu-id="c3368-657">Разверните структуру обмена сообщениями, хранящиеся в таблице и отобразить ее в виде графа.</span><span class="sxs-lookup"><span data-stu-id="c3368-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="c3368-658">Можно собирать данные и сохраните его в той же таблице, отображаемый более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="c3368-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c3368-659">Упражнение 2</span><span class="sxs-lookup"><span data-stu-id="c3368-659">Exercise 2</span></span>

<span data-ttu-id="c3368-660">Создайте дополнительный модуль «запись с камеры» для развертывания на доске Интернета вещей, таким образом, служба может записывать образы через камеру для анализа.</span><span class="sxs-lookup"><span data-stu-id="c3368-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
