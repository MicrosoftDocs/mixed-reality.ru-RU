---
title: Подключение к Wi-Fi в HoloLens
description: Инструкции по подключению к беспроводной сети Интернет с помощью HoloLens, а также по определению IP-адреса устройства.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, WiFi, беспроводная, Интернет, IP-адрес
ms.openlocfilehash: b064514124d861c0734ca51b3878d4a68b592fab
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670116"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="04287-104">Подключение к Wi-Fi в HoloLens</span><span class="sxs-lookup"><span data-stu-id="04287-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="04287-105">HoloLens содержит радиообмен Wi-Fi стандарта 802.11 с поддержкой AC.</span><span class="sxs-lookup"><span data-stu-id="04287-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="04287-106">Подключение HoloLens к сети Wi-Fi похоже на подключение настольного или мобильного устройства Windows 10 к сети Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="04287-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![Параметры Wi-Fi для HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="04287-108">Подключение к сети Wi-Fi в HoloLens</span><span class="sxs-lookup"><span data-stu-id="04287-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="04287-109">[Раскрытия](gestures.md#bloom) в меню " **Пуск** ".</span><span class="sxs-lookup"><span data-stu-id="04287-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="04287-110">Выберите приложение " **Параметры** " в меню "Пуск" или в списке " **все приложения** " справа от пункта "Пуск".</span><span class="sxs-lookup"><span data-stu-id="04287-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="04287-111">Приложение **параметров** будет размещено в автоматическом помещении.</span><span class="sxs-lookup"><span data-stu-id="04287-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="04287-112">Выберите **сеть & Интернет**.</span><span class="sxs-lookup"><span data-stu-id="04287-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="04287-113">Убедитесь, что функция Wi-Fi включена.</span><span class="sxs-lookup"><span data-stu-id="04287-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="04287-114">Выберите сеть Wi-Fi из списка.</span><span class="sxs-lookup"><span data-stu-id="04287-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="04287-115">Введите пароль сети Wi-Fi (при необходимости).</span><span class="sxs-lookup"><span data-stu-id="04287-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="04287-116">Отключение Wi-Fi в HoloLens</span><span class="sxs-lookup"><span data-stu-id="04287-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="04287-117">Использование приложения "Параметры" в HoloLens</span><span class="sxs-lookup"><span data-stu-id="04287-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="04287-118">[Раскрытия](gestures.md#bloom) в меню " **Пуск** ".</span><span class="sxs-lookup"><span data-stu-id="04287-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="04287-119">Выберите приложение " **Параметры** " в меню "Пуск" или в списке " **все приложения** " справа от пункта "Пуск".</span><span class="sxs-lookup"><span data-stu-id="04287-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="04287-120">Приложение **параметров** будет размещено в автоматическом помещении.</span><span class="sxs-lookup"><span data-stu-id="04287-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="04287-121">Выберите **сеть & Интернет**.</span><span class="sxs-lookup"><span data-stu-id="04287-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="04287-122">Выберите параметр ползунок Wi-Fi, чтобы переместить его в положение "Выкл.".</span><span class="sxs-lookup"><span data-stu-id="04287-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="04287-123">При этом компоненты RF радиостанции Wi-Fi будут отключены, а все функции Wi-Fi — в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="04287-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="04287-124">HoloLens не сможет автоматически загружать ваши [модули](environment-considerations-for-hololens.md#WiFi fingerprint considerations) при отключенном радиомодуле Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="04287-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#WiFi fingerprint considerations) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="04287-125">Переместите ползунок в положение "вкл.", чтобы включить радио Wi-Fi и восстановить функциональность Wi-Fi в Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="04287-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="04287-126">Выбранное состояние радиостанции Wi-Fi ("вкл" "отключено") будет сохраняться при перезагрузке.</span><span class="sxs-lookup"><span data-stu-id="04287-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="04287-127">Как проверить подключение к сети Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="04287-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="04287-128">[Раскрытия](gestures.md#bloom) , чтобы открыть меню " **Пуск** ".</span><span class="sxs-lookup"><span data-stu-id="04287-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="04287-129">Посмотрите на верхнюю левую часть меню Пуск для состояния Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="04287-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="04287-130">Будет отображено состояние Wi-Fi и SSID подключенной сети.</span><span class="sxs-lookup"><span data-stu-id="04287-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="04287-131">Определение IP-адреса HoloLens в сети Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="04287-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="04287-132">Использование приложения "Параметры"</span><span class="sxs-lookup"><span data-stu-id="04287-132">Using the Settings app</span></span>

1. <span data-ttu-id="04287-133">[Раскрытия](gestures.md#bloom) в меню " **Пуск** ".</span><span class="sxs-lookup"><span data-stu-id="04287-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="04287-134">Выберите приложение " **Параметры** " в меню "Пуск" или в списке " **все приложения** " справа от пункта "Пуск".</span><span class="sxs-lookup"><span data-stu-id="04287-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="04287-135">Приложение **параметров** будет размещено в автоматическом помещении.</span><span class="sxs-lookup"><span data-stu-id="04287-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="04287-136">Выберите **сеть & Интернет**.</span><span class="sxs-lookup"><span data-stu-id="04287-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="04287-137">Прокрутите вниз список доступных сетей Wi-Fi и выберите **свойства оборудования**.</span><span class="sxs-lookup"><span data-stu-id="04287-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Свойства оборудования в параметрах Wi-Fi](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="04287-139">IP-адрес будет отображаться рядом с **адресом IPv4**.</span><span class="sxs-lookup"><span data-stu-id="04287-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="04287-140">Использование Кортаны</span><span class="sxs-lookup"><span data-stu-id="04287-140">Using Cortana</span></span>

<span data-ttu-id="04287-141">Скажите: "*Привет, Кортана, мой IP-адрес?* "</span><span class="sxs-lookup"><span data-stu-id="04287-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="04287-142">и Кортана будет отображать и читать ваш IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="04287-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="04287-143">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="04287-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="04287-144">Откройте [портал устройств](using-the-windows-device-portal.md#networking) в веб-браузере на компьютере.</span><span class="sxs-lookup"><span data-stu-id="04287-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="04287-145">Перейдите к разделу " **сети** ".</span><span class="sxs-lookup"><span data-stu-id="04287-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="04287-146">Здесь будут отображаться IP-адрес и другие сведения о сети.</span><span class="sxs-lookup"><span data-stu-id="04287-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="04287-147">Этот метод позволяет легко копировать и вставлять IP-адреса на компьютере разработчика.</span><span class="sxs-lookup"><span data-stu-id="04287-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
