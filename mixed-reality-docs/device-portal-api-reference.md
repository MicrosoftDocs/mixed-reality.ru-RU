---
title: Портал устройств Справочник по API
description: Справочник по API для Windows Device Portal на HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal, API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694437"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="2580b-104">Портал устройств Справочник по API</span><span class="sxs-lookup"><span data-stu-id="2580b-104">Device portal API reference</span></span>

<span data-ttu-id="2580b-105">Все, что в [Windows Device Portal](using-the-windows-device-portal.md) построена на основе REST API можно использовать для доступа к данным и управления устройства программными средствами.</span><span class="sxs-lookup"><span data-stu-id="2580b-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="2580b-106">С развертыванием приложений</span><span class="sxs-lookup"><span data-stu-id="2580b-106">App deloyment</span></span>

<span data-ttu-id="2580b-107">**/API/App/packagemanager/Package (удаление)**</span><span class="sxs-lookup"><span data-stu-id="2580b-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="2580b-108">Удаляет приложение</span><span class="sxs-lookup"><span data-stu-id="2580b-108">Uninstalls an app</span></span>

<span data-ttu-id="2580b-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-109">Parameters</span></span>
* <span data-ttu-id="2580b-110">пакет: Имя файла пакета, который требуется удалить.</span><span class="sxs-lookup"><span data-stu-id="2580b-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="2580b-111">**/API/App/packagemanager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="2580b-112">Устанавливает приложение</span><span class="sxs-lookup"><span data-stu-id="2580b-112">Installs an App</span></span>

<span data-ttu-id="2580b-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-113">Parameters</span></span>
* <span data-ttu-id="2580b-114">пакет: Имя файла пакета должны быть установлены.</span><span class="sxs-lookup"><span data-stu-id="2580b-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="2580b-115">полезные данные</span><span class="sxs-lookup"><span data-stu-id="2580b-115">Payload</span></span>
* <span data-ttu-id="2580b-116">составной согласование основного текста http</span><span class="sxs-lookup"><span data-stu-id="2580b-116">multi-part conforming http body</span></span>

<span data-ttu-id="2580b-117">**/API/App/packagemanager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="2580b-118">Извлекает список установленных приложений в системе, с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="2580b-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="2580b-119">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-119">Return data</span></span>
* <span data-ttu-id="2580b-120">Список установленных пакетов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="2580b-120">List of installed packages with details</span></span>

<span data-ttu-id="2580b-121">**/API/App/packagemanager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="2580b-122">Возвращает состояние хода выполнения установки приложения</span><span class="sxs-lookup"><span data-stu-id="2580b-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="2580b-123">Коллекция дампов</span><span class="sxs-lookup"><span data-stu-id="2580b-123">Dump collection</span></span>

<span data-ttu-id="2580b-124">**/API/Debug/Dump/Usermode/CrashControl (удаление)**</span><span class="sxs-lookup"><span data-stu-id="2580b-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="2580b-125">Отключает сбор аварийных дампов для загрузка неопубликованного приложения</span><span class="sxs-lookup"><span data-stu-id="2580b-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="2580b-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-126">Parameters</span></span>
* <span data-ttu-id="2580b-127">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="2580b-127">packageFullname : package name</span></span>

<span data-ttu-id="2580b-128">**/API/Debug/Dump/Usermode/CrashControl (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="2580b-129">Возвращает параметры для неопубликованных приложений сбора аварийных дампов</span><span class="sxs-lookup"><span data-stu-id="2580b-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="2580b-130">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-130">Parameters</span></span>
* <span data-ttu-id="2580b-131">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="2580b-131">packageFullname : package name</span></span>

<span data-ttu-id="2580b-132">**/API/Debug/Dump/Usermode/CrashControl (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="2580b-133">Включает и задает параметры управления дампа для загрузка неопубликованного приложения</span><span class="sxs-lookup"><span data-stu-id="2580b-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="2580b-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-134">Parameters</span></span>
* <span data-ttu-id="2580b-135">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="2580b-135">packageFullname : package name</span></span>

<span data-ttu-id="2580b-136">**/API/Debug/Dump/Usermode/crashdump (удаление)**</span><span class="sxs-lookup"><span data-stu-id="2580b-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="2580b-137">Удаляет дампа для загрузка неопубликованного приложения</span><span class="sxs-lookup"><span data-stu-id="2580b-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="2580b-138">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-138">Parameters</span></span>
* <span data-ttu-id="2580b-139">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="2580b-139">packageFullname : package name</span></span>
* <span data-ttu-id="2580b-140">Имя файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="2580b-140">fileName : dump file name</span></span>

<span data-ttu-id="2580b-141">**/API/Debug/Dump/Usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="2580b-142">Извлекает дампа для загрузка неопубликованного приложения</span><span class="sxs-lookup"><span data-stu-id="2580b-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="2580b-143">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-143">Parameters</span></span>
* <span data-ttu-id="2580b-144">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="2580b-144">packageFullname : package name</span></span>
* <span data-ttu-id="2580b-145">Имя файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="2580b-145">fileName : dump file name</span></span>

<span data-ttu-id="2580b-146">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-146">Return data</span></span>
* <span data-ttu-id="2580b-147">Файл дампа.</span><span class="sxs-lookup"><span data-stu-id="2580b-147">Dump file.</span></span> <span data-ttu-id="2580b-148">Проверить с помощью Visual Studio или WinDbg</span><span class="sxs-lookup"><span data-stu-id="2580b-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="2580b-149">**/API/Debug/Dump/Usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="2580b-150">Возвращает список всех аварийных дампов для неопубликованных приложений</span><span class="sxs-lookup"><span data-stu-id="2580b-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="2580b-151">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-151">Return data</span></span>
* <span data-ttu-id="2580b-152">Список аварийных дампов на стороне загрузить приложение</span><span class="sxs-lookup"><span data-stu-id="2580b-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="2580b-153">Трассировка событий Windows</span><span class="sxs-lookup"><span data-stu-id="2580b-153">ETW</span></span>

<span data-ttu-id="2580b-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="2580b-155">Перечисляет зарегистрированных поставщиков</span><span class="sxs-lookup"><span data-stu-id="2580b-155">Enumerates registered providers</span></span>

<span data-ttu-id="2580b-156">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-156">Return data</span></span>
* <span data-ttu-id="2580b-157">Список поставщиков, понятное имя и идентификатор GUID</span><span class="sxs-lookup"><span data-stu-id="2580b-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="2580b-158">**/API/ETW/Session/RealTime (GET и WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2580b-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="2580b-159">Создает сеанс трассировки событий Windows в реальном времени; управлять через websocket.</span><span class="sxs-lookup"><span data-stu-id="2580b-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="2580b-160">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-160">Return data</span></span>
* <span data-ttu-id="2580b-161">События трассировки событий Windows из разрешенных поставщиков</span><span class="sxs-lookup"><span data-stu-id="2580b-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="2580b-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="2580b-162">Holographic OS</span></span>

<span data-ttu-id="2580b-163">**/API/holographic/OS/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="2580b-164">Возвращает список поставщиков трассировки событий Windows конкретного HoloLens, которые не зарегистрированы в системе</span><span class="sxs-lookup"><span data-stu-id="2580b-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="2580b-165">**/API/holographic/OS/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="2580b-166">Возвращает состояния всех служб, запущенных.</span><span class="sxs-lookup"><span data-stu-id="2580b-166">Returns the states of all services running.</span></span>

<span data-ttu-id="2580b-167">**/API/holographic/OS/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="2580b-168">Возвращает хранимые IPD (Interpupillary расстояние) в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="2580b-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="2580b-169">**/API/holographic/OS/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="2580b-170">Задает IPD</span><span class="sxs-lookup"><span data-stu-id="2580b-170">Sets the IPD</span></span>

<span data-ttu-id="2580b-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-171">Parameters</span></span>
* <span data-ttu-id="2580b-172">IPD: Новое значение IPD, задаваемый в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="2580b-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="2580b-173">**/API/holographic/OS/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="2580b-174">Получение требований HTTPS для Портала устройств</span><span class="sxs-lookup"><span data-stu-id="2580b-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="2580b-175">**/API/holographic/OS/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="2580b-176">Задает требования к HTTPS для портала устройства</span><span class="sxs-lookup"><span data-stu-id="2580b-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="2580b-177">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-177">Parameters</span></span>
* <span data-ttu-id="2580b-178">требуется: yes, нет или значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="2580b-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="2580b-179">Holographic восприятие</span><span class="sxs-lookup"><span data-stu-id="2580b-179">Holographic Perception</span></span>

<span data-ttu-id="2580b-180">**/API/holographic/perception/Client (GET и WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2580b-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="2580b-181">Принимает обновления websocket и запускает восприятие клиента, который отправляет обновления 30 кадров в секунду.</span><span class="sxs-lookup"><span data-stu-id="2580b-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="2580b-182">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-182">Parameters</span></span>
* <span data-ttu-id="2580b-183">clientmode: «активно» принудительно включает режим visual отслеживания при его не удается установить пассивно</span><span class="sxs-lookup"><span data-stu-id="2580b-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="2580b-184">Температурное holographic</span><span class="sxs-lookup"><span data-stu-id="2580b-184">Holographic Thermal</span></span>

<span data-ttu-id="2580b-185">**/API/holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="2580b-186">Получить температуры рабочей области устройства (обычный 0, 1 "горячего" резервирования, критические 2)</span><span class="sxs-lookup"><span data-stu-id="2580b-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="2580b-187">Элемент управления моделирования восприятие</span><span class="sxs-lookup"><span data-stu-id="2580b-187">Perception Simulation Control</span></span>

<span data-ttu-id="2580b-188">**/API/holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="2580b-189">Получение режима моделирования</span><span class="sxs-lookup"><span data-stu-id="2580b-189">Get the simulation mode</span></span>

<span data-ttu-id="2580b-190">**/API/holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="2580b-191">Установить режим моделирования</span><span class="sxs-lookup"><span data-stu-id="2580b-191">Set the simulation mode</span></span>

<span data-ttu-id="2580b-192">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-192">Parameters</span></span>
* <span data-ttu-id="2580b-193">режим: режиме моделирования: по умолчанию, моделирование, удаленное, прежних версий</span><span class="sxs-lookup"><span data-stu-id="2580b-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="2580b-194">**/API/holographic/Simulation/Control/Stream (удаление)**</span><span class="sxs-lookup"><span data-stu-id="2580b-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="2580b-195">Удалите поток управления.</span><span class="sxs-lookup"><span data-stu-id="2580b-195">Delete a control stream.</span></span>

<span data-ttu-id="2580b-196">**/API/holographic/Simulation/Control/Stream (GET и WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2580b-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="2580b-197">Откройте подключение веб-сокета для потока управления.</span><span class="sxs-lookup"><span data-stu-id="2580b-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="2580b-198">**/API/holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="2580b-199">Создание потока управления (приоритетом является обязательным) или отправки данных в созданный потока (streamId требуется).</span><span class="sxs-lookup"><span data-stu-id="2580b-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="2580b-200">Переданные данные должен иметь тип «application/octet-stream».</span><span class="sxs-lookup"><span data-stu-id="2580b-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="2580b-201">Воспроизведение моделирования восприятие</span><span class="sxs-lookup"><span data-stu-id="2580b-201">Perception Simulation Playback</span></span>

<span data-ttu-id="2580b-202">**/API/holographic/Simulation/Playback/File (удаление)**</span><span class="sxs-lookup"><span data-stu-id="2580b-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="2580b-203">Удаление записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-203">Delete a recording.</span></span>

<span data-ttu-id="2580b-204">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-204">Parameters</span></span>
* <span data-ttu-id="2580b-205">запись: Имя записи для удаления.</span><span class="sxs-lookup"><span data-stu-id="2580b-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="2580b-206">**/API/holographic/Simulation/Playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="2580b-207">Отправьте запись.</span><span class="sxs-lookup"><span data-stu-id="2580b-207">Upload a recording.</span></span>

<span data-ttu-id="2580b-208">**/API/holographic/Simulation/Playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="2580b-209">Получение всех записей.</span><span class="sxs-lookup"><span data-stu-id="2580b-209">Get all recordings.</span></span>

<span data-ttu-id="2580b-210">**/API/holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="2580b-211">Получите текущее состояние воспроизведения записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="2580b-212">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-212">Parameters</span></span>
* <span data-ttu-id="2580b-213">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-213">recording : Name of recording.</span></span>

<span data-ttu-id="2580b-214">**/API/holographic/Simulation/Playback/Session/File (удаление)**</span><span class="sxs-lookup"><span data-stu-id="2580b-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="2580b-215">Выгрузите операцию записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-215">Unload a recording.</span></span>

<span data-ttu-id="2580b-216">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-216">Parameters</span></span>
* <span data-ttu-id="2580b-217">запись: Имя записи для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="2580b-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="2580b-218">**/API/holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="2580b-219">Загрузите записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-219">Load a recording.</span></span>

<span data-ttu-id="2580b-220">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-220">Parameters</span></span>
* <span data-ttu-id="2580b-221">запись: Имя записи для загрузки.</span><span class="sxs-lookup"><span data-stu-id="2580b-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="2580b-222">**/API/holographic/Simulation/Playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="2580b-223">Получение всех загруженных записей.</span><span class="sxs-lookup"><span data-stu-id="2580b-223">Get all loaded recordings.</span></span>

<span data-ttu-id="2580b-224">**/API/holographic/Simulation/Playback/Session/Pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="2580b-225">Приостановите запись.</span><span class="sxs-lookup"><span data-stu-id="2580b-225">Pause a recording.</span></span>

<span data-ttu-id="2580b-226">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-226">Parameters</span></span>
* <span data-ttu-id="2580b-227">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-227">recording : Name of recording.</span></span>

<span data-ttu-id="2580b-228">**/API/holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="2580b-229">Воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="2580b-229">Play a recording.</span></span>

<span data-ttu-id="2580b-230">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-230">Parameters</span></span>
* <span data-ttu-id="2580b-231">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-231">recording : Name of recording.</span></span>

<span data-ttu-id="2580b-232">**/API/holographic/Simulation/Playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="2580b-233">Остановите запись.</span><span class="sxs-lookup"><span data-stu-id="2580b-233">Stop a recording.</span></span>

<span data-ttu-id="2580b-234">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-234">Parameters</span></span>
* <span data-ttu-id="2580b-235">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-235">recording : Name of recording.</span></span>

<span data-ttu-id="2580b-236">**/API/holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="2580b-237">Получите типы данных во время загрузки записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="2580b-238">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-238">Parameters</span></span>
* <span data-ttu-id="2580b-239">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="2580b-240">Запись моделирования восприятие</span><span class="sxs-lookup"><span data-stu-id="2580b-240">Perception Simulation Recording</span></span>

<span data-ttu-id="2580b-241">**/API/holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="2580b-242">Начните запись.</span><span class="sxs-lookup"><span data-stu-id="2580b-242">Start a recording.</span></span> <span data-ttu-id="2580b-243">Только одной записи могут быть активны одновременно.</span><span class="sxs-lookup"><span data-stu-id="2580b-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="2580b-244">Должно быть задано одно из head, руки, spatialMapping или среды.</span><span class="sxs-lookup"><span data-stu-id="2580b-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="2580b-245">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-245">Parameters</span></span>
* <span data-ttu-id="2580b-246">головной узел: Значение 1 для головного данные записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="2580b-247">Практическое. Значение 1 для записи данных вручную.</span><span class="sxs-lookup"><span data-stu-id="2580b-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="2580b-248">spatialMapping: Значение 1 для записи пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="2580b-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="2580b-249">Среда: Значение 1 для записи данных в среде.</span><span class="sxs-lookup"><span data-stu-id="2580b-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="2580b-250">Имя: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-250">name : Name of the recording.</span></span>
* <span data-ttu-id="2580b-251">singleSpatialMappingFrame: Значение 1 для записи только одно сопоставление пространственных кадра.</span><span class="sxs-lookup"><span data-stu-id="2580b-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="2580b-252">**/API/holographic/Simulation/Recording/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="2580b-253">Получить запись состояния.</span><span class="sxs-lookup"><span data-stu-id="2580b-253">Get recording state.</span></span>

<span data-ttu-id="2580b-254">**/API/holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="2580b-255">Остановите текущую запись.</span><span class="sxs-lookup"><span data-stu-id="2580b-255">Stop the current recording.</span></span> <span data-ttu-id="2580b-256">Запись будет возвращаться в виде файла.</span><span class="sxs-lookup"><span data-stu-id="2580b-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="2580b-257">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="2580b-257">Mixed Reality Capture</span></span>

<span data-ttu-id="2580b-258">**/API/holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="2580b-259">Загружает файл смешанной реальности из устройства.</span><span class="sxs-lookup"><span data-stu-id="2580b-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="2580b-260">Используйте op = параметр запроса потока для потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="2580b-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="2580b-261">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-261">Parameters</span></span>
* <span data-ttu-id="2580b-262">Имя файла: Имя, hex64, кодирования видео для получения файла</span><span class="sxs-lookup"><span data-stu-id="2580b-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="2580b-263">op: поток</span><span class="sxs-lookup"><span data-stu-id="2580b-263">op : stream</span></span>

<span data-ttu-id="2580b-264">**/API/holographic/MRC/File (удаление)**</span><span class="sxs-lookup"><span data-stu-id="2580b-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="2580b-265">Удаляет смешанной реальности, записи с устройства.</span><span class="sxs-lookup"><span data-stu-id="2580b-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="2580b-266">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-266">Parameters</span></span>
* <span data-ttu-id="2580b-267">Имя файла: Имя, hex64 кодировке файла для удаления</span><span class="sxs-lookup"><span data-stu-id="2580b-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="2580b-268">**/API/holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="2580b-269">Возвращает список файлов смешанной реальности, хранящихся на устройстве</span><span class="sxs-lookup"><span data-stu-id="2580b-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="2580b-270">**/API/holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="2580b-271">Делает снимок смешанной реальности и создает файл на устройстве</span><span class="sxs-lookup"><span data-stu-id="2580b-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="2580b-272">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-272">Parameters</span></span>
* <span data-ttu-id="2580b-273">holo: захват голограммы: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="2580b-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="2580b-274">PV: записи PV камеры: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="2580b-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="2580b-275">RenderFromCamera: Отрисовки (только для HoloLens 2) с точки зрения камеры фото и видео: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="2580b-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="2580b-276">**/API/holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="2580b-277">Получает значение по умолчанию смешанной реальности параметры записи</span><span class="sxs-lookup"><span data-stu-id="2580b-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="2580b-278">**/API/holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="2580b-279">Задает значение по умолчанию смешанной реальности параметры записи.</span><span class="sxs-lookup"><span data-stu-id="2580b-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="2580b-280">Некоторые из этих параметров применяются к фотографии MRC системы и видеозаписи.</span><span class="sxs-lookup"><span data-stu-id="2580b-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="2580b-281">**/API/holographic/MRC/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="2580b-282">Возвращает состояние смешанной реальности записи ("выполняется", "Остановлено")</span><span class="sxs-lookup"><span data-stu-id="2580b-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="2580b-283">**/API/holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="2580b-284">Возвращает эскиз для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="2580b-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="2580b-285">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-285">Parameters</span></span>
* <span data-ttu-id="2580b-286">Имя файла: Имя, hex64 в кодировке, для которого запрашивается эскиза файла</span><span class="sxs-lookup"><span data-stu-id="2580b-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="2580b-287">**/API/holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="2580b-288">Запускает запись смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="2580b-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="2580b-289">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-289">Parameters</span></span>
* <span data-ttu-id="2580b-290">holo: захват голограммы: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="2580b-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="2580b-291">PV: записи PV камеры: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="2580b-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="2580b-292">MIC: "микрофон" захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="2580b-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="2580b-293">замыкания на себя: запись звука приложения: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="2580b-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="2580b-294">RenderFromCamera: Отрисовки (только для HoloLens 2) с точки зрения камеры фото и видео: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="2580b-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="2580b-295">vstab: Стабилизации видео enable (только для HoloLens 2): true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="2580b-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="2580b-296">vstabbuffer: Задержка буфера стабилизации видео (только для HoloLens 2): 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="2580b-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="2580b-297">**/API/holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="2580b-298">Останавливает текущий смешанный записи реальность</span><span class="sxs-lookup"><span data-stu-id="2580b-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="2580b-299">Смешанная реальность потоковой передачи</span><span class="sxs-lookup"><span data-stu-id="2580b-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="2580b-300">HoloLens поддерживает интерактивный просмотр смешанной реальности через фрагментированный загрузки фрагментированного mp4.</span><span class="sxs-lookup"><span data-stu-id="2580b-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="2580b-301">Смешанная реальность потоки совместно используют тот же набор параметров для управления, что записывается:</span><span class="sxs-lookup"><span data-stu-id="2580b-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="2580b-302">holo: захват голограммы: true или false</span><span class="sxs-lookup"><span data-stu-id="2580b-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="2580b-303">PV: записи PV камеры: true или false</span><span class="sxs-lookup"><span data-stu-id="2580b-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="2580b-304">MIC: "микрофон" захвата: true или false</span><span class="sxs-lookup"><span data-stu-id="2580b-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="2580b-305">замыкания на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="2580b-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="2580b-306">Если не указан ни один из них: голограммы камеры фото и видео и аудио приложения будут записаны</span><span class="sxs-lookup"><span data-stu-id="2580b-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="2580b-307">Если указаны какие: Незаданные параметры по умолчанию используется значение false</span><span class="sxs-lookup"><span data-stu-id="2580b-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="2580b-308">Необязательные параметры (только для HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="2580b-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="2580b-309">RenderFromCamera: отрисовки с точки зрения камеры фото и видео: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="2580b-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="2580b-310">vstab: включить стабилизации видео: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="2580b-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="2580b-311">vstabbuffer: задержка буфера стабилизации видео: 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="2580b-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="2580b-312">**/API/holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="2580b-313">Поток 5Mbit 1280x720p 30 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="2580b-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="2580b-314">**/API/holographic/Stream/live_high.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="2580b-315">Поток 5Mbit 1280x720p 30 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="2580b-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="2580b-316">**/API/holographic/Stream/live_med.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="2580b-317">Поток 854x480p 2.5Mbit 30 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="2580b-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="2580b-318">**/API/holographic/Stream/live_low.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="2580b-319">Поток 428x240p 0.6Mbit 15 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="2580b-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="2580b-320">Сеть</span><span class="sxs-lookup"><span data-stu-id="2580b-320">Networking</span></span>

<span data-ttu-id="2580b-321">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="2580b-322">Возвращает текущую конфигурацию IP-адрес</span><span class="sxs-lookup"><span data-stu-id="2580b-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="2580b-323">Данные о ОС</span><span class="sxs-lookup"><span data-stu-id="2580b-323">OS Information</span></span>

<span data-ttu-id="2580b-324">**/API/OS/Info (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="2580b-325">Возвращает сведения об операционной системе</span><span class="sxs-lookup"><span data-stu-id="2580b-325">Gets operating system information</span></span>

<span data-ttu-id="2580b-326">**/API/OS/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="2580b-327">Получает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="2580b-327">Gets the machine name</span></span>

<span data-ttu-id="2580b-328">**/API/OS/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="2580b-329">Задает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="2580b-329">Sets the machine name</span></span>

<span data-ttu-id="2580b-330">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-330">Parameters</span></span>
* <span data-ttu-id="2580b-331">Имя: Новое имя компьютера, hex64 в кодировке, присвоено значение</span><span class="sxs-lookup"><span data-stu-id="2580b-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="2580b-332">Данные о производительности</span><span class="sxs-lookup"><span data-stu-id="2580b-332">Performance data</span></span>

<span data-ttu-id="2580b-333">**/API/ResourceManager/Processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="2580b-334">Возвращает список выполняющихся процессов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="2580b-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="2580b-335">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-335">Return data</span></span>
* <span data-ttu-id="2580b-336">JSON с помощью списка процессов и сведения для каждого процесса</span><span class="sxs-lookup"><span data-stu-id="2580b-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="2580b-337">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="2580b-338">Возвращает статистику производительности системы (операций ввода-вывода чтения и записи, Статистика использования памяти и т.д.</span><span class="sxs-lookup"><span data-stu-id="2580b-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="2580b-339">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-339">Return data</span></span>
* <span data-ttu-id="2580b-340">JSON с помощью сведений о системе: ЦП, графического Процессора, памяти, сети, операции ввода-ВЫВОДА</span><span class="sxs-lookup"><span data-stu-id="2580b-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="2580b-341">Питание</span><span class="sxs-lookup"><span data-stu-id="2580b-341">Power</span></span>

<span data-ttu-id="2580b-342">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="2580b-343">Возвращает текущее состояние батареи</span><span class="sxs-lookup"><span data-stu-id="2580b-343">Gets the current battery state</span></span>

<span data-ttu-id="2580b-344">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="2580b-345">Проверяет, находится ли система в состоянии пониженного энергопотребления</span><span class="sxs-lookup"><span data-stu-id="2580b-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="2580b-346">Удаленное управление</span><span class="sxs-lookup"><span data-stu-id="2580b-346">Remote Control</span></span>

<span data-ttu-id="2580b-347">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="2580b-348">Перезапускает целевого устройства</span><span class="sxs-lookup"><span data-stu-id="2580b-348">Restarts the target device</span></span>

<span data-ttu-id="2580b-349">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="2580b-350">Завершает работу целевого устройства</span><span class="sxs-lookup"><span data-stu-id="2580b-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="2580b-351">Диспетчер задач</span><span class="sxs-lookup"><span data-stu-id="2580b-351">Task Manager</span></span>

<span data-ttu-id="2580b-352">**/API/TaskManager/App (удаление)**</span><span class="sxs-lookup"><span data-stu-id="2580b-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="2580b-353">Останавливает современных приложений</span><span class="sxs-lookup"><span data-stu-id="2580b-353">Stops a modern app</span></span>

<span data-ttu-id="2580b-354">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-354">Parameters</span></span>
* <span data-ttu-id="2580b-355">пакет: Полное имя пакета приложения, hex64 кодировке</span><span class="sxs-lookup"><span data-stu-id="2580b-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="2580b-356">forcestop: Принудительно все процессы, чтобы остановить (= Да)</span><span class="sxs-lookup"><span data-stu-id="2580b-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="2580b-357">**/API/TaskManager/App (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="2580b-358">Запускает современных приложений</span><span class="sxs-lookup"><span data-stu-id="2580b-358">Starts a modern app</span></span>

<span data-ttu-id="2580b-359">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-359">Parameters</span></span>
* <span data-ttu-id="2580b-360">AppID: В кодировке hex64 PRAID приложения для запуска</span><span class="sxs-lookup"><span data-stu-id="2580b-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="2580b-361">пакет: Полное имя пакета приложения, hex64 кодировке</span><span class="sxs-lookup"><span data-stu-id="2580b-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="2580b-362">Управление Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="2580b-362">WiFi Management</span></span>

<span data-ttu-id="2580b-363">**/API/WiFi/Interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="2580b-364">Перечисляет беспроводных сетевых интерфейсов</span><span class="sxs-lookup"><span data-stu-id="2580b-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="2580b-365">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-365">Return data</span></span>
* <span data-ttu-id="2580b-366">Список беспроводных интерфейсах с подробными сведениями (идентификатор GUID, описание и т.д.)</span><span class="sxs-lookup"><span data-stu-id="2580b-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="2580b-367">**/API/WiFi/Network (удаление)**</span><span class="sxs-lookup"><span data-stu-id="2580b-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="2580b-368">Удаление профиля, связанные с сетью для указанного интерфейса</span><span class="sxs-lookup"><span data-stu-id="2580b-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="2580b-369">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-369">Parameters</span></span>
* <span data-ttu-id="2580b-370">интерфейс: сетевой интерфейс guid</span><span class="sxs-lookup"><span data-stu-id="2580b-370">interface : network interface guid</span></span>
* <span data-ttu-id="2580b-371">профиль: имя профиля</span><span class="sxs-lookup"><span data-stu-id="2580b-371">profile : profile name</span></span>

<span data-ttu-id="2580b-372">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="2580b-373">Перечисляет беспроводных сетей на указанного сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="2580b-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="2580b-374">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-374">Parameters</span></span>
* <span data-ttu-id="2580b-375">интерфейс: сетевой интерфейс guid</span><span class="sxs-lookup"><span data-stu-id="2580b-375">interface : network interface guid</span></span>

<span data-ttu-id="2580b-376">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-376">Return data</span></span>
* <span data-ttu-id="2580b-377">Список беспроводных сетей, найденных на интерфейсе с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="2580b-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="2580b-378">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="2580b-379">Подключении или отключении сети для указанного интерфейса</span><span class="sxs-lookup"><span data-stu-id="2580b-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="2580b-380">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-380">Parameters</span></span>
* <span data-ttu-id="2580b-381">интерфейс: сетевой интерфейс guid</span><span class="sxs-lookup"><span data-stu-id="2580b-381">interface : network interface guid</span></span>
* <span data-ttu-id="2580b-382">SSID: ssid, hex64 в кодировке, для подключения к</span><span class="sxs-lookup"><span data-stu-id="2580b-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="2580b-383">op: подключение и отключение</span><span class="sxs-lookup"><span data-stu-id="2580b-383">op : connect or disconnect</span></span>
* <span data-ttu-id="2580b-384">CreateProfile: Да или нет</span><span class="sxs-lookup"><span data-stu-id="2580b-384">createprofile : yes or no</span></span>
* <span data-ttu-id="2580b-385">ключ: общего ключа, hex64 кодировке</span><span class="sxs-lookup"><span data-stu-id="2580b-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="2580b-386">Средство записи производительности Windows</span><span class="sxs-lookup"><span data-stu-id="2580b-386">Windows Performance Recorder</span></span>

<span data-ttu-id="2580b-387">**/API/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="2580b-388">Передает WPR профиль и запускает трассировку с помощью загруженного профиля.</span><span class="sxs-lookup"><span data-stu-id="2580b-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="2580b-389">полезные данные</span><span class="sxs-lookup"><span data-stu-id="2580b-389">Payload</span></span>
* <span data-ttu-id="2580b-390">составной согласование основного текста http</span><span class="sxs-lookup"><span data-stu-id="2580b-390">multi-part conforming http body</span></span>

<span data-ttu-id="2580b-391">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-391">Return data</span></span>
* <span data-ttu-id="2580b-392">Возвращает состояние сеанса WPR.</span><span class="sxs-lookup"><span data-stu-id="2580b-392">Returns the WPR session status.</span></span>

<span data-ttu-id="2580b-393">**/API/wpr/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="2580b-394">Получает сведения о состоянии сеанса WPR</span><span class="sxs-lookup"><span data-stu-id="2580b-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="2580b-395">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-395">Return data</span></span>
* <span data-ttu-id="2580b-396">Состояние сеанса в WPR.</span><span class="sxs-lookup"><span data-stu-id="2580b-396">WPR session status.</span></span>

<span data-ttu-id="2580b-397">**/API/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="2580b-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="2580b-398">Останавливает сеанс трассировки WPR (производительность)</span><span class="sxs-lookup"><span data-stu-id="2580b-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="2580b-399">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-399">Return data</span></span>
* <span data-ttu-id="2580b-400">Возвращает ETL-файла трассировки</span><span class="sxs-lookup"><span data-stu-id="2580b-400">Returns the trace ETL file</span></span>

<span data-ttu-id="2580b-401">**/API/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="2580b-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="2580b-402">Запускает WPR (производительность), отслеживание сеансов</span><span class="sxs-lookup"><span data-stu-id="2580b-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="2580b-403">Параметры</span><span class="sxs-lookup"><span data-stu-id="2580b-403">Parameters</span></span>
* <span data-ttu-id="2580b-404">профиль: Имя профиля.</span><span class="sxs-lookup"><span data-stu-id="2580b-404">profile : Profile name.</span></span> <span data-ttu-id="2580b-405">Доступные профили хранятся в perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="2580b-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="2580b-406">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="2580b-406">Return data</span></span>
* <span data-ttu-id="2580b-407">При запуске возвращает состояние сеанса WPR.</span><span class="sxs-lookup"><span data-stu-id="2580b-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="2580b-408">См. также</span><span class="sxs-lookup"><span data-stu-id="2580b-408">See also</span></span>
* [<span data-ttu-id="2580b-409">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="2580b-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="2580b-410">Core портала устройства Справочник по API (UWP)</span><span class="sxs-lookup"><span data-stu-id="2580b-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
