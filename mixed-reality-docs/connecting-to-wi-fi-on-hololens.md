---
title: Подключение к Wi-Fi на HoloLens
description: Инструкции для подключения к беспроводной сети Интернет с HoloLens и как определить IP-адрес устройства.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: HoloLens, Wi-Fi, беспроводные сети, Интернет, IP-адрес, IP-адрес
ms.openlocfilehash: 0440c3dad48d73db51e7d730e79d6eb1e74a5694
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604111"
---
# <a name="connecting-to-wi-fi-on-hololens"></a><span data-ttu-id="c09ac-104">Подключение к Wi-Fi на HoloLens</span><span class="sxs-lookup"><span data-stu-id="c09ac-104">Connecting to Wi-Fi on HoloLens</span></span>

<span data-ttu-id="c09ac-105">HoloLens содержит 802.11 AC-2, поддержка x 2 Wi-Fi-радио.</span><span class="sxs-lookup"><span data-stu-id="c09ac-105">HoloLens contains a 802.11ac-capable, 2x2 Wi-Fi radio.</span></span> <span data-ttu-id="c09ac-106">Подключение к сети Wi-Fi, HoloLens похоже на подключение к сети Wi-Fi устройства с Windows 10 Desktop или Mobile.</span><span class="sxs-lookup"><span data-stu-id="c09ac-106">Connecting HoloLens to a Wi-Fi network is similar to connecting a Windows 10 Desktop or Mobile device to a Wi-Fi network.</span></span>

![Параметры Wi-Fi в HoloLens](images/wifi-hololens-600px.jpg)

## <a name="connecting-to-a-wi-fi-network-on-hololens"></a><span data-ttu-id="c09ac-108">Подключение к сети Wi-Fi на HoloLens</span><span class="sxs-lookup"><span data-stu-id="c09ac-108">Connecting to a Wi-Fi network on HoloLens</span></span>

1. <span data-ttu-id="c09ac-109">[Блума](gestures.md#bloom) для **запустить** меню.</span><span class="sxs-lookup"><span data-stu-id="c09ac-109">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="c09ac-110">Выберите **параметры** приложение с начала или из **все приложения** списка в правой части меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="c09ac-110">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="c09ac-111">**Параметры** приложение будет автоматически размещаемые перед глазами.</span><span class="sxs-lookup"><span data-stu-id="c09ac-111">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="c09ac-112">Выберите **сеть и Интернет**.</span><span class="sxs-lookup"><span data-stu-id="c09ac-112">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="c09ac-113">Убедитесь, что функция Wi-Fi включена.</span><span class="sxs-lookup"><span data-stu-id="c09ac-113">Make sure Wi-Fi is turned on.</span></span>
6. <span data-ttu-id="c09ac-114">Выберите сеть Wi-Fi в списке.</span><span class="sxs-lookup"><span data-stu-id="c09ac-114">Select a Wi-Fi network from the list.</span></span>
7. <span data-ttu-id="c09ac-115">Введите пароль сети Wi-Fi (при необходимости).</span><span class="sxs-lookup"><span data-stu-id="c09ac-115">Type in the Wi-Fi network password (if needed).</span></span>

## <a name="disabling-wi-fi-on-hololens"></a><span data-ttu-id="c09ac-116">Отключение Wi-Fi на HoloLens</span><span class="sxs-lookup"><span data-stu-id="c09ac-116">Disabling Wi-Fi on HoloLens</span></span>

### <a name="using-the-settings-app-on-hololens"></a><span data-ttu-id="c09ac-117">С помощью параметров приложения на HoloLens</span><span class="sxs-lookup"><span data-stu-id="c09ac-117">Using the Settings app on HoloLens</span></span>

1. <span data-ttu-id="c09ac-118">[Блума](gestures.md#bloom) для **запустить** меню.</span><span class="sxs-lookup"><span data-stu-id="c09ac-118">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="c09ac-119">Выберите **параметры** приложение с начала или из **все приложения** списка в правой части меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="c09ac-119">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="c09ac-120">**Параметры** приложение будет автоматически размещаемые перед глазами.</span><span class="sxs-lookup"><span data-stu-id="c09ac-120">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="c09ac-121">Выберите **сеть и Интернет**.</span><span class="sxs-lookup"><span data-stu-id="c09ac-121">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="c09ac-122">Выберите параметр "ползунок" Wi-Fi, чтобы переместить его в положение «Выкл.».</span><span class="sxs-lookup"><span data-stu-id="c09ac-122">Select the Wi-Fi slider switch to move it to the "Off" position.</span></span> <span data-ttu-id="c09ac-123">Это будет отключить компоненты RF Wi-Fi-радио и отключить все функциональные возможности Wi-Fi на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c09ac-123">This will turn off the RF components of the Wi-Fi radio and disable all Wi-Fi functionality on HoloLens.</span></span> 

    >[!WARNING]
    ><span data-ttu-id="c09ac-124">HoloLens, не смогут автоматически загружать вашей [пробелы](environment-considerations-for-hololens.md#spaces) при отключении Wi-Fi-радио.</span><span class="sxs-lookup"><span data-stu-id="c09ac-124">HoloLens will not be able to automatically load your [spaces](environment-considerations-for-hololens.md#spaces) when the Wi-Fi radio is disabled.</span></span>
    
6. <span data-ttu-id="c09ac-125">Переместите параметр ползунок в положение «Вкл.» Включение Wi-Fi-радио и восстановить функции Wi-Fi в Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c09ac-125">Move the slider switch to the "On" position to turn on the Wi-Fi radio and restore Wi-Fi functionality on Microsoft HoloLens.</span></span> <span data-ttu-id="c09ac-126">Выбранное состояние переключателя Wi-Fi («вкл.» из «Выкл.») будут сохраняться между перезагрузками.</span><span class="sxs-lookup"><span data-stu-id="c09ac-126">The selected Wi-Fi radio state ("On" of "Off") will persist across reboots.</span></span>

## <a name="how-to-confirm-you-are-connected-to-a-wi-fi-network"></a><span data-ttu-id="c09ac-127">Как проверить, вы подключены к сети Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="c09ac-127">How to confirm you are connected to a Wi-Fi network</span></span>

1. <span data-ttu-id="c09ac-128">[Блума](gestures.md#bloom) откроется **запустить** меню.</span><span class="sxs-lookup"><span data-stu-id="c09ac-128">[Bloom](gestures.md#bloom) to bring up the **Start** menu.</span></span>
2. <span data-ttu-id="c09ac-129">В верхней левой части меню "Пуск" для состояния Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="c09ac-129">Look at the top left of the Start menu for Wi-Fi status.</span></span> <span data-ttu-id="c09ac-130">Отображается состояние из Wi-Fi и идентификатор SSID подключенной сети.</span><span class="sxs-lookup"><span data-stu-id="c09ac-130">The state of Wi-Fi and the SSID of the connected network will be shown.</span></span>

## <a name="identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network"></a><span data-ttu-id="c09ac-131">Определение IP-адрес вашего HoloLens в сети Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="c09ac-131">Identifying the IP Address of your HoloLens on the Wi-Fi network</span></span>

### <a name="using-the-settings-app"></a><span data-ttu-id="c09ac-132">С помощью параметров приложения</span><span class="sxs-lookup"><span data-stu-id="c09ac-132">Using the Settings app</span></span>

1. <span data-ttu-id="c09ac-133">[Блума](gestures.md#bloom) для **запустить** меню.</span><span class="sxs-lookup"><span data-stu-id="c09ac-133">[Bloom](gestures.md#bloom) to the **Start** menu.</span></span>
2. <span data-ttu-id="c09ac-134">Выберите **параметры** приложение с начала или из **все приложения** списка в правой части меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="c09ac-134">Select the **Settings** app from Start or from the **All Apps** list on the right of the Start menu.</span></span>
3. <span data-ttu-id="c09ac-135">**Параметры** приложение будет автоматически размещаемые перед глазами.</span><span class="sxs-lookup"><span data-stu-id="c09ac-135">The **Settings** app will be auto-placed in front of you.</span></span>
4. <span data-ttu-id="c09ac-136">Выберите **сеть и Интернет**.</span><span class="sxs-lookup"><span data-stu-id="c09ac-136">Select **Network & Internet**.</span></span>
5. <span data-ttu-id="c09ac-137">Прокрутите вниз до раздела под списком доступных сетей Wi-Fi и выберите **свойства оборудования**.</span><span class="sxs-lookup"><span data-stu-id="c09ac-137">Scroll down to beneath the list of available Wi-Fi networks and select **Hardware properties**.</span></span>

    ![Свойства оборудования в параметры Wi-Fi](images/wifi-hololens-hwdetails.jpg)

<span data-ttu-id="c09ac-139">IP-адрес будет отображаться рядом с полем **IPv4-адрес**.</span><span class="sxs-lookup"><span data-stu-id="c09ac-139">The IP address will be shown next to **IPv4 address**.</span></span>

### <a name="using-cortana"></a><span data-ttu-id="c09ac-140">С помощью Кортаны</span><span class="sxs-lookup"><span data-stu-id="c09ac-140">Using Cortana</span></span>

<span data-ttu-id="c09ac-141">Скажем «*Привет, Кортана, что такое Мой IP-адрес?*"</span><span class="sxs-lookup"><span data-stu-id="c09ac-141">Say "*Hey Cortana, What's my IP address?*"</span></span> <span data-ttu-id="c09ac-142">и Cortana отображает и читает вслух IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="c09ac-142">and Cortana will display and read out your IP address.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="c09ac-143">С помощью Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="c09ac-143">Using Windows Device Portal</span></span>

1. <span data-ttu-id="c09ac-144">Откройте [портал устройств](using-the-windows-device-portal.md#networking) через веб-браузер на Компьютере.</span><span class="sxs-lookup"><span data-stu-id="c09ac-144">Open the [device portal](using-the-windows-device-portal.md#networking) in a web browser on your PC.</span></span>
2. <span data-ttu-id="c09ac-145">Перейдите к **сети** раздел.</span><span class="sxs-lookup"><span data-stu-id="c09ac-145">Navigate to the **Networking** section.</span></span>

<span data-ttu-id="c09ac-146">IP-адрес и другие сведения о сети будут отображены.</span><span class="sxs-lookup"><span data-stu-id="c09ac-146">Your IP address and other network information will be displayed there.</span></span> <span data-ttu-id="c09ac-147">Этот метод позволяет легко копировать и вставить IP-адреса на Компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="c09ac-147">This method allows for easy copy and paste of the IP address on your development PC.</span></span>
