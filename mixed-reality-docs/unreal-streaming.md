---
title: Потоковая передача в Unreal
description: Руководство по потоковой передаче в Unreal для HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, потоковая передача, компьютер, голографическое удаленное взаимодействие с приложением, проигрыватель для голографического удаленного взаимодействия, документация
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: d25efbcf83e45749cc4eb8b99581b71105c59c9d
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303535"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="25d64-104">Потоковая передача в Unreal</span><span class="sxs-lookup"><span data-stu-id="25d64-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="25d64-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="25d64-105">Overview</span></span>
<span data-ttu-id="25d64-106">Потоковая передача с компьютера в HoloLens обеспечивает два основных преимущества:</span><span class="sxs-lookup"><span data-stu-id="25d64-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="25d64-107">Ваше приложение смешанной реальности может использовать вычислительные мощности компьютера.</span><span class="sxs-lookup"><span data-stu-id="25d64-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="25d64-108">Ускоренная итерация разработки.</span><span class="sxs-lookup"><span data-stu-id="25d64-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="25d64-109">Чтобы приступить к работе, скачайте [Holographic Remoting Player](holographic-remoting-player.md) на устройство HoloLens.</span><span class="sxs-lookup"><span data-stu-id="25d64-109">To get started, you'll need to download the [Holographic Remoting Player](holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="25d64-110">Этот инструмент позволит вашему приложению передавать данные в потоковом режиме непосредственно на проигрыватель удаленного взаимодействия на HoloLens из следующих источников:</span><span class="sxs-lookup"><span data-stu-id="25d64-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="25d64-111">редактор Unreal Engine;</span><span class="sxs-lookup"><span data-stu-id="25d64-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="25d64-112">упакованный исполняемый файл Windows.</span><span class="sxs-lookup"><span data-stu-id="25d64-112">A packaged Windows executable</span></span> 

<span data-ttu-id="25d64-113">При потоковой передаче вы получаете доступ практически ко всем возможностям HoloLens, которые можно использовать при запуске приложения на устройстве.</span><span class="sxs-lookup"><span data-stu-id="25d64-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="25d64-114">К ним относятся [отслеживание суставов рук](unreal-hand-tracking.md) (если вы используете HoloLens 2), [пространственное картирование](unreal-spatial-mapping.md) и [пространственные привязки](unreal-spatial-anchors.md). Но при этом недоступны функции из этого [списка ограничений](holographic-remoting-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="25d64-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="25d64-115">Качество потоковой передачи в значительной степени зависит от уровня сигнала вашей беспроводной сети.</span><span class="sxs-lookup"><span data-stu-id="25d64-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="25d64-116">Все возможности автоматически включаются в приложении Holographic Remoting Player.</span><span class="sxs-lookup"><span data-stu-id="25d64-116">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="25d64-117">Если вы обнаружите возможность, для включения которой требуется разрешение пользователя (например, отслеживание движения глаз) при потоковой передаче, но не при выполнении на устройстве, убедитесь, что вы включили необходимые возможности в параметрах проекта.</span><span class="sxs-lookup"><span data-stu-id="25d64-117">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="25d64-118">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="25d64-118">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="25d64-119"><strong>Источник</strong></span><span class="sxs-lookup"><span data-stu-id="25d64-119"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="25d64-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1-го поколения</strong></a></span><span class="sxs-lookup"><span data-stu-id="25d64-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="25d64-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="25d64-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="25d64-122"><strong>Иммерсивные гарнитуры</strong></span><span class="sxs-lookup"><span data-stu-id="25d64-122"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="25d64-123">Unreal Editor</span><span class="sxs-lookup"><span data-stu-id="25d64-123">Unreal editor</span></span></td>
        <td><span data-ttu-id="25d64-124">✔️</span><span class="sxs-lookup"><span data-stu-id="25d64-124">✔️</span></span></td>
        <td><span data-ttu-id="25d64-125">✔️</span><span class="sxs-lookup"><span data-stu-id="25d64-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="25d64-126">Пакет Windows</span><span class="sxs-lookup"><span data-stu-id="25d64-126">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="25d64-127">✔️</span><span class="sxs-lookup"><span data-stu-id="25d64-127">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="25d64-128">Потоковая передача из Unreal Editor</span><span class="sxs-lookup"><span data-stu-id="25d64-128">Streaming from the Unreal editor</span></span>

<span data-ttu-id="25d64-129">Потоковая передача данных из Unreal Editor на устройство HoloLens обеспечивает разработчикам значительные преимущества при тестировании, а именно отсутствие необходимости ждать, пока приложение будет собрано и развернуто, для оценки обновлений.</span><span class="sxs-lookup"><span data-stu-id="25d64-129">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="25d64-130">Подробные инструкции по [потоковой передаче из Unreal Editor](unreal-uxt-ch6.md#device-only-streaming) можно найти в последнем разделе серии руководств по началу работы с Unreal.</span><span class="sxs-lookup"><span data-stu-id="25d64-130">You can find detailed instructions on [streaming from the Unreal editor](unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="25d64-131">Потоковая передача из упакованного исполняемого файла Windows</span><span class="sxs-lookup"><span data-stu-id="25d64-131">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="25d64-132">Начиная с версии Unreal 4.25.1, вы можете передавать данные вашего приложения на устройство HoloLens 2 в потоковом режиме из упакованного исполняемого файла Windows, выполнив следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="25d64-132">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="25d64-133">Выберите **File > Package Project > Windows** (Файл > Проект пакета > Windows) в меню редактора.</span><span class="sxs-lookup"><span data-stu-id="25d64-133">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="25d64-134">Выберите расположение для сохранения пакета и нажмите **Select Folder** (Выбрать папку).</span><span class="sxs-lookup"><span data-stu-id="25d64-134">Choose a location to save your package and click **Select Folder**.</span></span>

2. <span data-ttu-id="25d64-135">После завершения сборки пакета откройте инструмент **Holographic Remoting Player** на HoloLens 2 и запишите значение IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="25d64-135">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="25d64-136">Оставьте **Holographic Remoting Player** открытым и с помощью командной строки выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="25d64-136">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="25d64-137">С помощью команды cd перейдите в локальный каталог с сохраненным пакетом.</span><span class="sxs-lookup"><span data-stu-id="25d64-137">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="25d64-138">Введите следующую команду: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="25d64-138">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="25d64-139">Имя приложения в параметрах проекта должно быть автоматически использовано для создания пакета Windows.</span><span class="sxs-lookup"><span data-stu-id="25d64-139">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="25d64-140">Если по какой-либо причине имена отличаются, используйте имя исполняемого файла Windows в командной строке.</span><span class="sxs-lookup"><span data-stu-id="25d64-140">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="25d64-141">Нажмите клавишу ВВОД, и ваше приложение начнет потоковую передачу.</span><span class="sxs-lookup"><span data-stu-id="25d64-141">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="25d64-142">См. также статью</span><span class="sxs-lookup"><span data-stu-id="25d64-142">See also</span></span>
* [<span data-ttu-id="25d64-143">История версий голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="25d64-143">Holographic remoting version history</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="25d64-144">Создание пользовательского проигрывателя для голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="25d64-144">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="25d64-145">Установка безопасного подключения с использованием голографического удаленного взаимодействия</span><span class="sxs-lookup"><span data-stu-id="25d64-145">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
