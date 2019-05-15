---
title: Восстановить в HoloLens
description: Основные и дополнительные инструкции для перезагрузки или Сброс к HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Практическое руководство, перезагрузка, сброс, восстановление, аппаратный сброс "," теплую "," Цикл электропитания, HoloLens, завершение работы
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599879"
---
# <a name="reset-or-recover-your-hololens"></a><span data-ttu-id="a9292-104">Восстановить в HoloLens</span><span class="sxs-lookup"><span data-stu-id="a9292-104">Reset or recover your HoloLens</span></span>

<span data-ttu-id="a9292-105">Если у вас возникли проблемы, с вашей HoloLens, может потребоваться попробовать перезагрузка, сброс или даже повторно flash с помощью восстановления устройства.</span><span class="sxs-lookup"><span data-stu-id="a9292-105">If you’re experiencing problems with your HoloLens you may want to try a restart, reset, or even re-flash with device recovery.</span></span> <span data-ttu-id="a9292-106">Этот документ поможет выполнить рекомендуемые действия последовательно.</span><span class="sxs-lookup"><span data-stu-id="a9292-106">This document will guide you through the recommended steps in succession.</span></span>

## <a name="perform-a-device-reboot"></a><span data-ttu-id="a9292-107">Выполнять перезагрузку устройства</span><span class="sxs-lookup"><span data-stu-id="a9292-107">Perform a device reboot</span></span>

<span data-ttu-id="a9292-108">Если ваш HoloLens возникли проблемы или не отвечает, сначала попробуйте перезагрузить его с помощью одного из указанных ниже методов.</span><span class="sxs-lookup"><span data-stu-id="a9292-108">If your HoloLens is experiencing issues or is unresponsive, first try rebooting it via one of the below methods.</span></span>

### <a name="perform-a-safe-reboot-via-cortana"></a><span data-ttu-id="a9292-109">Выполнить безопасный перезагрузку через Cortana</span><span class="sxs-lookup"><span data-stu-id="a9292-109">Perform a safe reboot via Cortana</span></span>

<span data-ttu-id="a9292-110">Наиболее безопасным способом перезагрузить HoloLens — с помощью Кортаны.</span><span class="sxs-lookup"><span data-stu-id="a9292-110">The safest way to reboot the HoloLens is via Cortana.</span></span> <span data-ttu-id="a9292-111">Обычно это отличный первый шаг при возникновении проблемы с HoloLens:</span><span class="sxs-lookup"><span data-stu-id="a9292-111">This is generally a great first-step when experiencing an issue with HoloLens:</span></span>
1. <span data-ttu-id="a9292-112">Поместите на устройстве</span><span class="sxs-lookup"><span data-stu-id="a9292-112">Put on your device</span></span>
2. <span data-ttu-id="a9292-113">Убедитесь в том, что оно включено, пользователь в систему и не ожидает пароль для разблокировки устройства.</span><span class="sxs-lookup"><span data-stu-id="a9292-113">Make sure it’s powered on, a user is logged in, and the device is not waiting for a password to unlock it.</span></span>
3. <span data-ttu-id="a9292-114">Предположим, что «Привет, Кортана, перезагрузите» или «Привет, Кортана, перезапустите.»</span><span class="sxs-lookup"><span data-stu-id="a9292-114">Say “Hey Cortana, reboot” or "Hey Cortana, restart."</span></span>
4. <span data-ttu-id="a9292-115">Когда она подтверждает она запросит подтверждение.</span><span class="sxs-lookup"><span data-stu-id="a9292-115">When she acknowledges she will ask you for confirmation.</span></span> <span data-ttu-id="a9292-116">Подождите минутку для звук после она свой вопрос, указывающее, что она ожидает вам и произнесите «Да».</span><span class="sxs-lookup"><span data-stu-id="a9292-116">Wait a second for a sound to play after she has finished her question, indicating she is listening to you and then say “Yes.”</span></span>
5. <span data-ttu-id="a9292-117">Устройство будет теперь перезагрузки/restart.</span><span class="sxs-lookup"><span data-stu-id="a9292-117">The device will now reboot/restart.</span></span>

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a><span data-ttu-id="a9292-118">Выполнить безопасный перезагрузку через Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="a9292-118">Perform a safe reboot via Windows Device Portal</span></span>

<span data-ttu-id="a9292-119">Если оно не работает, попробуйте перезагрузить устройство через [Windows Device Portal](using-the-windows-device-portal.md).</span><span class="sxs-lookup"><span data-stu-id="a9292-119">If the above doesn't work, you can try to reboot the device via [Windows Device Portal](using-the-windows-device-portal.md).</span></span> <span data-ttu-id="a9292-120">В правом верхнем углу есть параметр перезагрузку или отключение устройства.</span><span class="sxs-lookup"><span data-stu-id="a9292-120">In the upper right corner, there is an option to restart/shutdown the device.</span></span>

### <a name="perform-a-safe-reboot-via-the-power-button"></a><span data-ttu-id="a9292-121">Выполнить перезагрузку безопасно с помощью кнопки питания</span><span class="sxs-lookup"><span data-stu-id="a9292-121">Perform a safe reboot via the power button</span></span>

<span data-ttu-id="a9292-122">Если вы по-прежнему не удается перезагрузить устройство, можно попытаться выполнить перезагрузку, с помощью кнопки питания:</span><span class="sxs-lookup"><span data-stu-id="a9292-122">If you still can't reboot your device, you can try to issue a reboot via the power button:</span></span>
1. <span data-ttu-id="a9292-123">Нажмите и удерживайте кнопку питания на 5 секунд</span><span class="sxs-lookup"><span data-stu-id="a9292-123">Press and hold the power button for 5 seconds</span></span>
   1. <span data-ttu-id="a9292-124">Через 1 секунду вы увидите все 5 освещают Светодиодные индикаторы, затем медленно выключить справа налево</span><span class="sxs-lookup"><span data-stu-id="a9292-124">After 1 second, you will see all 5 LEDs illuminate, then slowly turn off from right to left</span></span>
   2. <span data-ttu-id="a9292-125">Через 5 секунд всех светодиодных индикаторов будет отключать, указывающий, что успешно использовалась команда завершения работы</span><span class="sxs-lookup"><span data-stu-id="a9292-125">After 5 seconds, all LEDs will be off, indicating the shutdown command was issued successfully</span></span>
   3. <span data-ttu-id="a9292-126">Обратите внимание, что необходимо остановить, нажав кнопку сразу же после всех индикаторов отключали функцию</span><span class="sxs-lookup"><span data-stu-id="a9292-126">Note, it’s important to stop pressing the button immediately after all the LEDs have turned off</span></span>
2. <span data-ttu-id="a9292-127">Подождите 1 минуту аккуратно успешного завершения работы.</span><span class="sxs-lookup"><span data-stu-id="a9292-127">Wait 1 minute for the shutdown to cleanly succeed.</span></span> <span data-ttu-id="a9292-128">Обратите внимание, что завершение работы по-прежнему может быть в процессе выполнения, даже если отключены дисплеев</span><span class="sxs-lookup"><span data-stu-id="a9292-128">Note that the shutdown may still be in progress even if the displays are off</span></span>
3. <span data-ttu-id="a9292-129">Питания на устройстве еще раз, нажав и удерживая кнопку питания в течение 1 секунды</span><span class="sxs-lookup"><span data-stu-id="a9292-129">Power on the device again by pressing and holding the power button for 1 second</span></span>

### <a name="perform-an-unsafe-forced-reboot"></a><span data-ttu-id="a9292-130">Выполните небезопасный Принудительная перезагрузка</span><span class="sxs-lookup"><span data-stu-id="a9292-130">Perform an unsafe forced reboot</span></span>

<span data-ttu-id="a9292-131">Если ни один из указанных способов не сможет успешно перезагрузить устройство, вы можете принудительно перезагрузить компьютер.</span><span class="sxs-lookup"><span data-stu-id="a9292-131">If none of the above methods are able to successfully reboot your device, you can force a reboot.</span></span> <span data-ttu-id="a9292-132">Обратите внимание, что этот метод эквивалентен извлечение аккумулятора из HoloLens и таким образом, является опасной операцией, что может оставить устройство в поврежденном состоянии.</span><span class="sxs-lookup"><span data-stu-id="a9292-132">Note that this method is equivalent to pulling the battery from the HoloLens, and as such, is a dangerous operation which may leave your device in a corrupt state.</span></span> 

>[!WARNING]
><span data-ttu-id="a9292-133">Это потенциально опасные метод и должен использоваться только в случае не работает ни одно из указанных способов.</span><span class="sxs-lookup"><span data-stu-id="a9292-133">This is a potentially harmful method and should only be used in the event none of the above methods work.</span></span>

1. <span data-ttu-id="a9292-134">Нажмите и удерживайте кнопку питания, в течение 10 секунд</span><span class="sxs-lookup"><span data-stu-id="a9292-134">Press and hold the power button for at least 10 seconds</span></span>
   * <span data-ttu-id="a9292-135">Вполне допустимо удерживать кнопку для более 10 секунд</span><span class="sxs-lookup"><span data-stu-id="a9292-135">It’s okay to hold the button for longer than 10 seconds</span></span>
   * <span data-ttu-id="a9292-136">Его можно не учитывать все Индикаторы активности</span><span class="sxs-lookup"><span data-stu-id="a9292-136">It’s safe to ignore any LED activity</span></span>
2. <span data-ttu-id="a9292-137">Отпустите кнопку и подождите 2 – 3 секунды</span><span class="sxs-lookup"><span data-stu-id="a9292-137">Release the button and wait 2-3 seconds</span></span>
3. <span data-ttu-id="a9292-138">Питания на устройстве еще раз, нажав и удерживая кнопку питания в течение 1 секунды</span><span class="sxs-lookup"><span data-stu-id="a9292-138">Power on the device again by pressing and holding the power button for 1 second</span></span>

## <a name="reset-the-device-to-a-factory-clean-state"></a><span data-ttu-id="a9292-139">Сброс устройства до очистки состояния фабрики</span><span class="sxs-lookup"><span data-stu-id="a9292-139">Reset the device to a factory clean state</span></span>

<span data-ttu-id="a9292-140">Если ваш HoloLens по-прежнему возникают проблемы с после перезагрузки, попробуйте сбросить его в исходное состояние фабрики.</span><span class="sxs-lookup"><span data-stu-id="a9292-140">If your HoloLens is still experiencing issues after rebooting, you can try resetting it to a factory clean state.</span></span> <span data-ttu-id="a9292-141">При сбросе вашего устройства, будут удалены все персональные данные, приложения и параметры.</span><span class="sxs-lookup"><span data-stu-id="a9292-141">If you reset your device, all your personal data, apps, and settings will be erased.</span></span> <span data-ttu-id="a9292-142">Сброс только установит последнюю установленную версию Windows Holographic и необходимо будет повторить все этапы инициализации (калибровка, подключения к Wi-Fi, создайте учетную запись пользователя, загрузите приложения и т. д...).</span><span class="sxs-lookup"><span data-stu-id="a9292-142">Resetting will only install the latest installed version of Windows Holographic and you will have to redo all the initialization steps (calibrate, connect to WiFi, create a user account, download apps, etc…).</span></span>
1. <span data-ttu-id="a9292-143">Запустите **параметры** "->" приложение **обновление** -> **сброса**</span><span class="sxs-lookup"><span data-stu-id="a9292-143">Launch the **Settings** app -> **Update** -> **Reset**</span></span>
2. <span data-ttu-id="a9292-144">Выберите **устройства с восстановленными** параметр и чтение диалоговое окно подтверждения</span><span class="sxs-lookup"><span data-stu-id="a9292-144">Select the **Reset device** option and read the confirmation dialog</span></span>
3. <span data-ttu-id="a9292-145">Если вы согласны, для сброса параметров устройства, устройство перезагрузится и отобразить набор вращается шестеренки с индикатор хода выполнения</span><span class="sxs-lookup"><span data-stu-id="a9292-145">If you agree to reset your device, the device will reboot and display a set of spinning gears with a progress bar</span></span>
4. <span data-ttu-id="a9292-146">Подождите около 30 минут для завершения этого процесса</span><span class="sxs-lookup"><span data-stu-id="a9292-146">Wait about 30 minutes for this process to complete</span></span>
5. <span data-ttu-id="a9292-147">Сброс завершается, и устройство будет перезагружен в готовой установки и настройки</span><span class="sxs-lookup"><span data-stu-id="a9292-147">The reset will complete and the device will reboot into the out of the box experience</span></span>

## <a name="perform-a-full-device-recovery"></a><span data-ttu-id="a9292-148">Выполните восстановление полной устройства</span><span class="sxs-lookup"><span data-stu-id="a9292-148">Perform a full device recovery</span></span>

<span data-ttu-id="a9292-149">Если после выполнения перечисленных выше, устройство не соответствует **по-прежнему** заморожена, не отвечает, или возникли проблемы обновления или программного обеспечения можно восстановить его с помощью Windows Device Recovery Tool.</span><span class="sxs-lookup"><span data-stu-id="a9292-149">If, after performing the above options, your device is **still** frozen, unresponsive, or experiencing update or software problems you can recover it using the Windows Device Recovery Tool.</span></span> <span data-ttu-id="a9292-150">Восстановление устройства похоже на возврат в том смысле, что будут удалены все содержимое пользователя на устройстве, включая приложения, игры, фотографии, учетные записи пользователей и многое другое.</span><span class="sxs-lookup"><span data-stu-id="a9292-150">Recovering your device is similar to resetting it in the sense that it will erase all user content on the device, including apps, games, photos, user accounts, and more.</span></span> <span data-ttu-id="a9292-151">Если это возможно создайте резервную копию любые сведения, которые вы хотите сохранить.</span><span class="sxs-lookup"><span data-stu-id="a9292-151">If possible, backup any information you want to keep.</span></span>

<span data-ttu-id="a9292-152">Чтобы полностью восстановить ваши HoloLens:</span><span class="sxs-lookup"><span data-stu-id="a9292-152">To fully recover your HoloLens:</span></span>
1. <span data-ttu-id="a9292-153">Отключить все телефоны и устройства Windows с компьютера</span><span class="sxs-lookup"><span data-stu-id="a9292-153">Disconnect all phones and Windows devices from your PC</span></span>
2. <span data-ttu-id="a9292-154">Установите и запустите [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) на ПК</span><span class="sxs-lookup"><span data-stu-id="a9292-154">Install and launch the [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) on your PC</span></span>
3. <span data-ttu-id="a9292-155">Подключиться к Компьютеру с помощью micro-USB-кабель с вашей HoloLens</span><span class="sxs-lookup"><span data-stu-id="a9292-155">Connect your HoloLens to your PC using the micro-USB cable it came with</span></span>
   * <span data-ttu-id="a9292-156">Обратите внимание на то, что не все USB-кабели создаются равными.</span><span class="sxs-lookup"><span data-stu-id="a9292-156">Note that not all USB cables are created equal.</span></span> <span data-ttu-id="a9292-157">Даже если вы уже использовали другой кабель успешно, этот поток будет предоставлять новые состояния, где кабель может выполняться медленнее.</span><span class="sxs-lookup"><span data-stu-id="a9292-157">Even if you’ve been using another cable successfully, this flow will expose new states where the cable may not perform as well.</span></span> <span data-ttu-id="a9292-158">То, которое прилагается к HoloLens является лучшим и наиболее хорошо протестированные параметр</span><span class="sxs-lookup"><span data-stu-id="a9292-158">The one your HoloLens came with is the best and most well tested option</span></span>
4. <span data-ttu-id="a9292-159">Если средство автоматически определит ваше устройство, оно будет отображаться Плитка HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a9292-159">If the tool automatically detects your device it will display a HoloLens tile.</span></span> <span data-ttu-id="a9292-160">Щелкните его и следуйте инструкциям, чтобы завершить процесс</span><span class="sxs-lookup"><span data-stu-id="a9292-160">Click it and follow the instructions to complete the process</span></span>

>[!NOTE]
><span data-ttu-id="a9292-161">WDRT может восстановить устройство для более ранней версии Windows Holographic; может потребоваться установить обновления после обновления</span><span class="sxs-lookup"><span data-stu-id="a9292-161">WDRT may recover your device to an older version of Windows Holographic; you may need to install updates after flashing</span></span>

<span data-ttu-id="a9292-162">Если средство не удается автоматически обнаружить устройства, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="a9292-162">If the tool is unable to detect your device automatically, try the following:</span></span>
1. <span data-ttu-id="a9292-163">Перезагрузить ПК и повторите попытку (это устраняет большинство проблем)</span><span class="sxs-lookup"><span data-stu-id="a9292-163">Reboot your PC and try again (this fixes most issues)</span></span>
2. <span data-ttu-id="a9292-164">Нажмите кнопку **устройство не обнаружена кнопка**, выберите **Microsoft HoloLens**и следуйте инструкциям на экране</span><span class="sxs-lookup"><span data-stu-id="a9292-164">Click the **My device was not detected button**, choose **Microsoft HoloLens**, and follow the rest of the instructions on the screen</span></span>