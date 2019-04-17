---
title: Портал устройств Справочник по API
description: Справочник по API для Windows Device Portal на HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Device Portal, API
ms.openlocfilehash: 507ab98734adea80d0aad41d99124e3d91846f28
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603279"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="82694-104">Портал устройств Справочник по API</span><span class="sxs-lookup"><span data-stu-id="82694-104">Device portal API reference</span></span>

<span data-ttu-id="82694-105">Все, что в [Windows Device Portal](using-the-windows-device-portal.md) построена на основе REST API можно использовать для доступа к данным и управления устройства программными средствами.</span><span class="sxs-lookup"><span data-stu-id="82694-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="82694-106">С развертыванием приложений</span><span class="sxs-lookup"><span data-stu-id="82694-106">App deloyment</span></span>

<span data-ttu-id="82694-107">**/API/App/packagemanager/Package (удаление)**</span><span class="sxs-lookup"><span data-stu-id="82694-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="82694-108">Удаляет приложение</span><span class="sxs-lookup"><span data-stu-id="82694-108">Uninstalls an app</span></span>

<span data-ttu-id="82694-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-109">Parameters</span></span>
* <span data-ttu-id="82694-110">пакет: Имя файла пакета, который требуется удалить.</span><span class="sxs-lookup"><span data-stu-id="82694-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="82694-111">**/API/App/packagemanager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="82694-112">Устанавливает приложение</span><span class="sxs-lookup"><span data-stu-id="82694-112">Installs an App</span></span>

<span data-ttu-id="82694-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-113">Parameters</span></span>
* <span data-ttu-id="82694-114">пакет: Имя файла пакета должны быть установлены.</span><span class="sxs-lookup"><span data-stu-id="82694-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="82694-115">полезные данные</span><span class="sxs-lookup"><span data-stu-id="82694-115">Payload</span></span>
* <span data-ttu-id="82694-116">составной согласование основного текста http</span><span class="sxs-lookup"><span data-stu-id="82694-116">multi-part conforming http body</span></span>

<span data-ttu-id="82694-117">**/API/App/packagemanager/Packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="82694-118">Извлекает список установленных приложений в системе, с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="82694-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="82694-119">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-119">Return data</span></span>
* <span data-ttu-id="82694-120">Список установленных пакетов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="82694-120">List of installed packages with details</span></span>

<span data-ttu-id="82694-121">**/API/App/packagemanager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="82694-122">Возвращает состояние хода выполнения установки приложения</span><span class="sxs-lookup"><span data-stu-id="82694-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="82694-123">Коллекция дампов</span><span class="sxs-lookup"><span data-stu-id="82694-123">Dump collection</span></span>

<span data-ttu-id="82694-124">**/API/Debug/Dump/Usermode/CrashControl (удаление)**</span><span class="sxs-lookup"><span data-stu-id="82694-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="82694-125">Отключает сбор аварийных дампов для загрузка неопубликованного приложения</span><span class="sxs-lookup"><span data-stu-id="82694-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="82694-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-126">Parameters</span></span>
* <span data-ttu-id="82694-127">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="82694-127">packageFullname : package name</span></span>

<span data-ttu-id="82694-128">**/API/Debug/Dump/Usermode/CrashControl (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="82694-129">Возвращает параметры для неопубликованных приложений сбора аварийных дампов</span><span class="sxs-lookup"><span data-stu-id="82694-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="82694-130">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-130">Parameters</span></span>
* <span data-ttu-id="82694-131">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="82694-131">packageFullname : package name</span></span>

<span data-ttu-id="82694-132">**/API/Debug/Dump/Usermode/CrashControl (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="82694-133">Включает и задает параметры управления дампа для загрузка неопубликованного приложения</span><span class="sxs-lookup"><span data-stu-id="82694-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="82694-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-134">Parameters</span></span>
* <span data-ttu-id="82694-135">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="82694-135">packageFullname : package name</span></span>

<span data-ttu-id="82694-136">**/API/Debug/Dump/Usermode/crashdump (удаление)**</span><span class="sxs-lookup"><span data-stu-id="82694-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="82694-137">Удаляет дампа для загрузка неопубликованного приложения</span><span class="sxs-lookup"><span data-stu-id="82694-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="82694-138">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-138">Parameters</span></span>
* <span data-ttu-id="82694-139">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="82694-139">packageFullname : package name</span></span>
* <span data-ttu-id="82694-140">Имя файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="82694-140">fileName : dump file name</span></span>

<span data-ttu-id="82694-141">**/API/Debug/Dump/Usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="82694-142">Извлекает дампа для загрузка неопубликованного приложения</span><span class="sxs-lookup"><span data-stu-id="82694-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="82694-143">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-143">Parameters</span></span>
* <span data-ttu-id="82694-144">"полноеимяпакета": имя пакета</span><span class="sxs-lookup"><span data-stu-id="82694-144">packageFullname : package name</span></span>
* <span data-ttu-id="82694-145">Имя файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="82694-145">fileName : dump file name</span></span>

<span data-ttu-id="82694-146">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-146">Return data</span></span>
* <span data-ttu-id="82694-147">Файл дампа.</span><span class="sxs-lookup"><span data-stu-id="82694-147">Dump file.</span></span> <span data-ttu-id="82694-148">Проверить с помощью Visual Studio или WinDbg</span><span class="sxs-lookup"><span data-stu-id="82694-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="82694-149">**/API/Debug/Dump/Usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="82694-150">Возвращает список всех аварийных дампов для неопубликованных приложений</span><span class="sxs-lookup"><span data-stu-id="82694-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="82694-151">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-151">Return data</span></span>
* <span data-ttu-id="82694-152">Список аварийных дампов на стороне загрузить приложение</span><span class="sxs-lookup"><span data-stu-id="82694-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="82694-153">Трассировка событий Windows</span><span class="sxs-lookup"><span data-stu-id="82694-153">ETW</span></span>

<span data-ttu-id="82694-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="82694-155">Перечисляет зарегистрированных поставщиков</span><span class="sxs-lookup"><span data-stu-id="82694-155">Enumerates registered providers</span></span>

<span data-ttu-id="82694-156">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-156">Return data</span></span>
* <span data-ttu-id="82694-157">Список поставщиков, понятное имя и идентификатор GUID</span><span class="sxs-lookup"><span data-stu-id="82694-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="82694-158">**/API/ETW/Session/RealTime (GET и WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="82694-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="82694-159">Создает сеанс трассировки событий Windows в реальном времени; управлять через websocket.</span><span class="sxs-lookup"><span data-stu-id="82694-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="82694-160">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-160">Return data</span></span>
* <span data-ttu-id="82694-161">События трассировки событий Windows из разрешенных поставщиков</span><span class="sxs-lookup"><span data-stu-id="82694-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="82694-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="82694-162">Holographic OS</span></span>

<span data-ttu-id="82694-163">**/API/holographic/OS/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="82694-164">Возвращает список поставщиков трассировки событий Windows конкретного HoloLens, которые не зарегистрированы в системе</span><span class="sxs-lookup"><span data-stu-id="82694-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="82694-165">**/API/holographic/OS/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="82694-166">Возвращает состояния всех служб, запущенных.</span><span class="sxs-lookup"><span data-stu-id="82694-166">Returns the states of all services running.</span></span>

<span data-ttu-id="82694-167">**/API/holographic/OS/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="82694-168">Возвращает хранимые IPD (Interpupillary расстояние) в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="82694-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="82694-169">**/API/holographic/OS/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="82694-170">Задает IPD</span><span class="sxs-lookup"><span data-stu-id="82694-170">Sets the IPD</span></span>

<span data-ttu-id="82694-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-171">Parameters</span></span>
* <span data-ttu-id="82694-172">IPD: Новое значение IPD, задаваемый в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="82694-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="82694-173">**/API/holographic/OS/webmanagement/Settings/HTTPS (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="82694-174">Получение требований HTTPS для Портала устройств</span><span class="sxs-lookup"><span data-stu-id="82694-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="82694-175">**/API/holographic/OS/webmanagement/Settings/HTTPS (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="82694-176">Задает требования к HTTPS для портала устройства</span><span class="sxs-lookup"><span data-stu-id="82694-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="82694-177">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-177">Parameters</span></span>
* <span data-ttu-id="82694-178">требуется: yes, нет или значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="82694-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="82694-179">Holographic восприятие</span><span class="sxs-lookup"><span data-stu-id="82694-179">Holographic Perception</span></span>

<span data-ttu-id="82694-180">**/API/holographic/perception/Client (GET и WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="82694-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="82694-181">Принимает обновления websocket и запускает восприятие клиента, который отправляет обновления 30 кадров в секунду.</span><span class="sxs-lookup"><span data-stu-id="82694-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="82694-182">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-182">Parameters</span></span>
* <span data-ttu-id="82694-183">clientmode: «активно» принудительно включает режим visual отслеживания при его не удается установить пассивно</span><span class="sxs-lookup"><span data-stu-id="82694-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="82694-184">Температурное holographic</span><span class="sxs-lookup"><span data-stu-id="82694-184">Holographic Thermal</span></span>

<span data-ttu-id="82694-185">**/API/holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="82694-186">Получить температуры рабочей области устройства (обычный 0, 1 "горячего" резервирования, критические 2)</span><span class="sxs-lookup"><span data-stu-id="82694-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="82694-187">Элемент управления моделирования восприятие</span><span class="sxs-lookup"><span data-stu-id="82694-187">Perception Simulation Control</span></span>

<span data-ttu-id="82694-188">**/API/holographic/Simulation/Control/Mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="82694-189">Получение режима моделирования</span><span class="sxs-lookup"><span data-stu-id="82694-189">Get the simulation mode</span></span>

<span data-ttu-id="82694-190">**/API/holographic/Simulation/Control/Mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="82694-191">Установить режим моделирования</span><span class="sxs-lookup"><span data-stu-id="82694-191">Set the simulation mode</span></span>

<span data-ttu-id="82694-192">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-192">Parameters</span></span>
* <span data-ttu-id="82694-193">режим: режиме моделирования: по умолчанию, моделирование, удаленное, прежних версий</span><span class="sxs-lookup"><span data-stu-id="82694-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="82694-194">**/API/holographic/Simulation/Control/Stream (удаление)**</span><span class="sxs-lookup"><span data-stu-id="82694-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="82694-195">Удалите поток управления.</span><span class="sxs-lookup"><span data-stu-id="82694-195">Delete a control stream.</span></span>

<span data-ttu-id="82694-196">**/API/holographic/Simulation/Control/Stream (GET и WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="82694-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="82694-197">Откройте подключение веб-сокета для потока управления.</span><span class="sxs-lookup"><span data-stu-id="82694-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="82694-198">**/API/holographic/Simulation/Control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="82694-199">Создание потока управления (приоритетом является обязательным) или отправки данных в созданный потока (streamId требуется).</span><span class="sxs-lookup"><span data-stu-id="82694-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="82694-200">Переданные данные должен иметь тип «application/octet-stream».</span><span class="sxs-lookup"><span data-stu-id="82694-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="82694-201">Воспроизведение моделирования восприятие</span><span class="sxs-lookup"><span data-stu-id="82694-201">Perception Simulation Playback</span></span>

<span data-ttu-id="82694-202">**/API/holographic/Simulation/Playback/File (удаление)**</span><span class="sxs-lookup"><span data-stu-id="82694-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="82694-203">Удаление записи.</span><span class="sxs-lookup"><span data-stu-id="82694-203">Delete a recording.</span></span>

<span data-ttu-id="82694-204">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-204">Parameters</span></span>
* <span data-ttu-id="82694-205">запись: Имя записи для удаления.</span><span class="sxs-lookup"><span data-stu-id="82694-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="82694-206">**/API/holographic/Simulation/Playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="82694-207">Отправьте запись.</span><span class="sxs-lookup"><span data-stu-id="82694-207">Upload a recording.</span></span>

<span data-ttu-id="82694-208">**/API/holographic/Simulation/Playback/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="82694-209">Получение всех записей.</span><span class="sxs-lookup"><span data-stu-id="82694-209">Get all recordings.</span></span>

<span data-ttu-id="82694-210">**/API/holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="82694-211">Получите текущее состояние воспроизведения записи.</span><span class="sxs-lookup"><span data-stu-id="82694-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="82694-212">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-212">Parameters</span></span>
* <span data-ttu-id="82694-213">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="82694-213">recording : Name of recording.</span></span>

<span data-ttu-id="82694-214">**/API/holographic/Simulation/Playback/Session/File (удаление)**</span><span class="sxs-lookup"><span data-stu-id="82694-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="82694-215">Выгрузите операцию записи.</span><span class="sxs-lookup"><span data-stu-id="82694-215">Unload a recording.</span></span>

<span data-ttu-id="82694-216">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-216">Parameters</span></span>
* <span data-ttu-id="82694-217">запись: Имя записи для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="82694-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="82694-218">**/API/holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="82694-219">Загрузите записи.</span><span class="sxs-lookup"><span data-stu-id="82694-219">Load a recording.</span></span>

<span data-ttu-id="82694-220">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-220">Parameters</span></span>
* <span data-ttu-id="82694-221">запись: Имя записи для загрузки.</span><span class="sxs-lookup"><span data-stu-id="82694-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="82694-222">**/API/holographic/Simulation/Playback/Session/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="82694-223">Получение всех загруженных записей.</span><span class="sxs-lookup"><span data-stu-id="82694-223">Get all loaded recordings.</span></span>

<span data-ttu-id="82694-224">**/API/holographic/Simulation/Playback/Session/Pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="82694-225">Приостановите запись.</span><span class="sxs-lookup"><span data-stu-id="82694-225">Pause a recording.</span></span>

<span data-ttu-id="82694-226">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-226">Parameters</span></span>
* <span data-ttu-id="82694-227">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="82694-227">recording : Name of recording.</span></span>

<span data-ttu-id="82694-228">**/API/holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="82694-229">Воспроизвести.</span><span class="sxs-lookup"><span data-stu-id="82694-229">Play a recording.</span></span>

<span data-ttu-id="82694-230">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-230">Parameters</span></span>
* <span data-ttu-id="82694-231">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="82694-231">recording : Name of recording.</span></span>

<span data-ttu-id="82694-232">**/API/holographic/Simulation/Playback/Session/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="82694-233">Остановите запись.</span><span class="sxs-lookup"><span data-stu-id="82694-233">Stop a recording.</span></span>

<span data-ttu-id="82694-234">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-234">Parameters</span></span>
* <span data-ttu-id="82694-235">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="82694-235">recording : Name of recording.</span></span>

<span data-ttu-id="82694-236">**/API/holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="82694-237">Получите типы данных во время загрузки записи.</span><span class="sxs-lookup"><span data-stu-id="82694-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="82694-238">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-238">Parameters</span></span>
* <span data-ttu-id="82694-239">запись: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="82694-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="82694-240">Запись моделирования восприятие</span><span class="sxs-lookup"><span data-stu-id="82694-240">Perception Simulation Recording</span></span>

<span data-ttu-id="82694-241">**/API/holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="82694-242">Начните запись.</span><span class="sxs-lookup"><span data-stu-id="82694-242">Start a recording.</span></span> <span data-ttu-id="82694-243">Только одной записи могут быть активны одновременно.</span><span class="sxs-lookup"><span data-stu-id="82694-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="82694-244">Должно быть задано одно из head, руки, spatialMapping или среды.</span><span class="sxs-lookup"><span data-stu-id="82694-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="82694-245">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-245">Parameters</span></span>
* <span data-ttu-id="82694-246">головной узел: Значение 1 для головного данные записи.</span><span class="sxs-lookup"><span data-stu-id="82694-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="82694-247">Практическое. Значение 1 для записи данных вручную.</span><span class="sxs-lookup"><span data-stu-id="82694-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="82694-248">spatialMapping: Значение 1 для записи пространственное сопоставление.</span><span class="sxs-lookup"><span data-stu-id="82694-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="82694-249">Среда: Значение 1 для записи данных в среде.</span><span class="sxs-lookup"><span data-stu-id="82694-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="82694-250">Имя: Имя записи.</span><span class="sxs-lookup"><span data-stu-id="82694-250">name : Name of the recording.</span></span>
* <span data-ttu-id="82694-251">singleSpatialMappingFrame: Значение 1 для записи только одно сопоставление пространственных кадра.</span><span class="sxs-lookup"><span data-stu-id="82694-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="82694-252">**/API/holographic/Simulation/Recording/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="82694-253">Получить запись состояния.</span><span class="sxs-lookup"><span data-stu-id="82694-253">Get recording state.</span></span>

<span data-ttu-id="82694-254">**/API/holographic/Simulation/Recording/Stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="82694-255">Остановите текущую запись.</span><span class="sxs-lookup"><span data-stu-id="82694-255">Stop the current recording.</span></span> <span data-ttu-id="82694-256">Запись будет возвращаться в виде файла.</span><span class="sxs-lookup"><span data-stu-id="82694-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="82694-257">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="82694-257">Mixed Reality Capture</span></span>

<span data-ttu-id="82694-258">**/API/holographic/MRC/File (удаление)**</span><span class="sxs-lookup"><span data-stu-id="82694-258">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="82694-259">Удаляет смешанной реальности, записи с устройства.</span><span class="sxs-lookup"><span data-stu-id="82694-259">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="82694-260">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-260">Parameters</span></span>
* <span data-ttu-id="82694-261">Имя файла: Имя, hex64 кодировке файла для удаления</span><span class="sxs-lookup"><span data-stu-id="82694-261">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="82694-262">**/API/holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-262">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="82694-263">Получает значение по умолчанию смешанной реальности параметры записи</span><span class="sxs-lookup"><span data-stu-id="82694-263">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="82694-264">**/API/holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-264">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="82694-265">Загружает файл смешанной реальности из устройства.</span><span class="sxs-lookup"><span data-stu-id="82694-265">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="82694-266">Используйте op = параметр запроса потока для потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="82694-266">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="82694-267">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-267">Parameters</span></span>
* <span data-ttu-id="82694-268">Имя файла: Имя, hex64, кодирования видео для получения файла</span><span class="sxs-lookup"><span data-stu-id="82694-268">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="82694-269">op: поток</span><span class="sxs-lookup"><span data-stu-id="82694-269">op : stream</span></span>

<span data-ttu-id="82694-270">**/API/holographic/MRC/Thumbnail (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-270">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="82694-271">Возвращает эскиз для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="82694-271">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="82694-272">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-272">Parameters</span></span>
* <span data-ttu-id="82694-273">Имя файла: Имя, hex64 в кодировке, для которого запрашивается эскиза файла</span><span class="sxs-lookup"><span data-stu-id="82694-273">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="82694-274">**/API/holographic/MRC/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-274">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="82694-275">Возвращает состояние смешанной реальности записи ("выполняется", "Остановлено")</span><span class="sxs-lookup"><span data-stu-id="82694-275">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="82694-276">**/API/holographic/MRC/Files (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-276">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="82694-277">Возвращает список файлов смешанной реальности, хранящихся на устройстве</span><span class="sxs-lookup"><span data-stu-id="82694-277">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="82694-278">**/API/holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="82694-279">Задает значение по умолчанию смешанной реальности параметры записи</span><span class="sxs-lookup"><span data-stu-id="82694-279">Sets the default mixed reality capture settings</span></span>

<span data-ttu-id="82694-280">**/API/holographic/MRC/Video/Control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-280">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="82694-281">Запускает запись смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="82694-281">Starts a mixed reality recording</span></span>

<span data-ttu-id="82694-282">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-282">Parameters</span></span>
* <span data-ttu-id="82694-283">holo: захват голограммы: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-283">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="82694-284">PV: записи PV камеры: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-284">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="82694-285">MIC: "микрофон" захвата: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-285">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="82694-286">замыкания на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-286">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="82694-287">**/API/holographic/MRC/Video/Control/Stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-287">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="82694-288">Останавливает текущий смешанный записи реальность</span><span class="sxs-lookup"><span data-stu-id="82694-288">Stops the current mixed reality recording</span></span>

<span data-ttu-id="82694-289">**/API/holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-289">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="82694-290">Делает снимок смешанной реальности и создает файл на устройстве</span><span class="sxs-lookup"><span data-stu-id="82694-290">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="82694-291">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-291">Parameters</span></span>
* <span data-ttu-id="82694-292">holo: захват голограммы: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-292">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="82694-293">PV: записи PV камеры: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-293">pv : capture PV camera: true or false</span></span>

<span data-ttu-id="82694-294">Смешанная реальность потоковой передачи</span><span class="sxs-lookup"><span data-stu-id="82694-294">Mixed Reality Streaming</span></span>

<span data-ttu-id="82694-295">**/API/holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-295">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="82694-296">Инициализация поблочной загрузки фрагментированного файла MP4</span><span class="sxs-lookup"><span data-stu-id="82694-296">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="82694-297">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-297">Parameters</span></span>
* <span data-ttu-id="82694-298">holo: захват голограммы: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-298">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="82694-299">PV: записи PV камеры: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-299">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="82694-300">MIC: "микрофон" захвата: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-300">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="82694-301">замыкания на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-301">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="82694-302">**/API/holographic/Stream/live_high.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-302">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="82694-303">Инициализация поблочной загрузки фрагментированного файла MP4</span><span class="sxs-lookup"><span data-stu-id="82694-303">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="82694-304">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-304">Parameters</span></span>
* <span data-ttu-id="82694-305">holo: захват голограммы: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="82694-306">PV: записи PV камеры: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="82694-307">MIC: "микрофон" захвата: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="82694-308">замыкания на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="82694-309">**/API/holographic/Stream/live_low.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-309">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="82694-310">Инициализация поблочной загрузки фрагментированного файла MP4</span><span class="sxs-lookup"><span data-stu-id="82694-310">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="82694-311">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-311">Parameters</span></span>
* <span data-ttu-id="82694-312">holo: захват голограммы: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-312">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="82694-313">PV: записи PV камеры: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-313">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="82694-314">MIC: "микрофон" захвата: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-314">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="82694-315">замыкания на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-315">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="82694-316">**/API/holographic/Stream/live_med.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="82694-317">Инициализация поблочной загрузки фрагментированного файла MP4</span><span class="sxs-lookup"><span data-stu-id="82694-317">Initiates a chunked download of a fragmented mp4</span></span>

<span data-ttu-id="82694-318">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-318">Parameters</span></span>
* <span data-ttu-id="82694-319">holo: захват голограммы: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-319">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="82694-320">PV: записи PV камеры: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-320">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="82694-321">MIC: "микрофон" захвата: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-321">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="82694-322">замыкания на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="82694-322">loopback : capture app audio: true or false</span></span>

## <a name="networking"></a><span data-ttu-id="82694-323">Сеть</span><span class="sxs-lookup"><span data-stu-id="82694-323">Networking</span></span>

<span data-ttu-id="82694-324">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="82694-325">Возвращает текущую конфигурацию IP-адрес</span><span class="sxs-lookup"><span data-stu-id="82694-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="82694-326">Данные о ОС</span><span class="sxs-lookup"><span data-stu-id="82694-326">OS Information</span></span>

<span data-ttu-id="82694-327">**/API/OS/Info (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="82694-328">Возвращает сведения об операционной системе</span><span class="sxs-lookup"><span data-stu-id="82694-328">Gets operating system information</span></span>

<span data-ttu-id="82694-329">**/API/OS/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="82694-330">Получает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="82694-330">Gets the machine name</span></span>

<span data-ttu-id="82694-331">**/API/OS/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="82694-332">Задает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="82694-332">Sets the machine name</span></span>

<span data-ttu-id="82694-333">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-333">Parameters</span></span>
* <span data-ttu-id="82694-334">Имя: Новое имя компьютера, hex64 в кодировке, присвоено значение</span><span class="sxs-lookup"><span data-stu-id="82694-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="82694-335">Данные о производительности</span><span class="sxs-lookup"><span data-stu-id="82694-335">Performance data</span></span>

<span data-ttu-id="82694-336">**/API/ResourceManager/Processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="82694-337">Возвращает список выполняющихся процессов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="82694-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="82694-338">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-338">Return data</span></span>
* <span data-ttu-id="82694-339">JSON с помощью списка процессов и сведения для каждого процесса</span><span class="sxs-lookup"><span data-stu-id="82694-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="82694-340">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="82694-341">Возвращает статистику производительности системы (операций ввода-вывода чтения и записи, Статистика использования памяти и т.д.</span><span class="sxs-lookup"><span data-stu-id="82694-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="82694-342">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-342">Return data</span></span>
* <span data-ttu-id="82694-343">JSON с помощью сведений о системе: ЦП, графического Процессора, памяти, сети, операции ввода-ВЫВОДА</span><span class="sxs-lookup"><span data-stu-id="82694-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="82694-344">Питание</span><span class="sxs-lookup"><span data-stu-id="82694-344">Power</span></span>

<span data-ttu-id="82694-345">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="82694-346">Возвращает текущее состояние батареи</span><span class="sxs-lookup"><span data-stu-id="82694-346">Gets the current battery state</span></span>

<span data-ttu-id="82694-347">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="82694-348">Проверяет, находится ли система в состоянии пониженного энергопотребления</span><span class="sxs-lookup"><span data-stu-id="82694-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="82694-349">Удаленное управление</span><span class="sxs-lookup"><span data-stu-id="82694-349">Remote Control</span></span>

<span data-ttu-id="82694-350">**/API/Control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="82694-351">Перезапускает целевого устройства</span><span class="sxs-lookup"><span data-stu-id="82694-351">Restarts the target device</span></span>

<span data-ttu-id="82694-352">**/API/Control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="82694-353">Завершает работу целевого устройства</span><span class="sxs-lookup"><span data-stu-id="82694-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="82694-354">Диспетчер задач</span><span class="sxs-lookup"><span data-stu-id="82694-354">Task Manager</span></span>

<span data-ttu-id="82694-355">**/API/TaskManager/App (удаление)**</span><span class="sxs-lookup"><span data-stu-id="82694-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="82694-356">Останавливает современных приложений</span><span class="sxs-lookup"><span data-stu-id="82694-356">Stops a modern app</span></span>

<span data-ttu-id="82694-357">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-357">Parameters</span></span>
* <span data-ttu-id="82694-358">пакет: Полное имя пакета приложения, hex64 кодировке</span><span class="sxs-lookup"><span data-stu-id="82694-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="82694-359">forcestop: Принудительно все процессы, чтобы остановить (= Да)</span><span class="sxs-lookup"><span data-stu-id="82694-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="82694-360">**/API/TaskManager/App (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="82694-361">Запускает современных приложений</span><span class="sxs-lookup"><span data-stu-id="82694-361">Starts a modern app</span></span>

<span data-ttu-id="82694-362">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-362">Parameters</span></span>
* <span data-ttu-id="82694-363">AppID: В кодировке hex64 PRAID приложения для запуска</span><span class="sxs-lookup"><span data-stu-id="82694-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="82694-364">пакет: Полное имя пакета приложения, hex64 кодировке</span><span class="sxs-lookup"><span data-stu-id="82694-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="82694-365">Управление Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="82694-365">WiFi Management</span></span>

<span data-ttu-id="82694-366">**/API/WiFi/Interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="82694-367">Перечисляет беспроводных сетевых интерфейсов</span><span class="sxs-lookup"><span data-stu-id="82694-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="82694-368">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-368">Return data</span></span>
* <span data-ttu-id="82694-369">Список беспроводных интерфейсах с подробными сведениями (идентификатор GUID, описание и т.д.)</span><span class="sxs-lookup"><span data-stu-id="82694-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="82694-370">**/API/WiFi/Network (удаление)**</span><span class="sxs-lookup"><span data-stu-id="82694-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="82694-371">Удаление профиля, связанные с сетью для указанного интерфейса</span><span class="sxs-lookup"><span data-stu-id="82694-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="82694-372">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-372">Parameters</span></span>
* <span data-ttu-id="82694-373">интерфейс: сетевой интерфейс guid</span><span class="sxs-lookup"><span data-stu-id="82694-373">interface : network interface guid</span></span>
* <span data-ttu-id="82694-374">профиль: имя профиля</span><span class="sxs-lookup"><span data-stu-id="82694-374">profile : profile name</span></span>

<span data-ttu-id="82694-375">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="82694-376">Перечисляет беспроводных сетей на указанного сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="82694-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="82694-377">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-377">Parameters</span></span>
* <span data-ttu-id="82694-378">интерфейс: сетевой интерфейс guid</span><span class="sxs-lookup"><span data-stu-id="82694-378">interface : network interface guid</span></span>

<span data-ttu-id="82694-379">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-379">Return data</span></span>
* <span data-ttu-id="82694-380">Список беспроводных сетей, найденных на интерфейсе с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="82694-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="82694-381">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="82694-382">Подключении или отключении сети для указанного интерфейса</span><span class="sxs-lookup"><span data-stu-id="82694-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="82694-383">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-383">Parameters</span></span>
* <span data-ttu-id="82694-384">интерфейс: сетевой интерфейс guid</span><span class="sxs-lookup"><span data-stu-id="82694-384">interface : network interface guid</span></span>
* <span data-ttu-id="82694-385">SSID: ssid, hex64 в кодировке, для подключения к</span><span class="sxs-lookup"><span data-stu-id="82694-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="82694-386">op: подключение и отключение</span><span class="sxs-lookup"><span data-stu-id="82694-386">op : connect or disconnect</span></span>
* <span data-ttu-id="82694-387">CreateProfile: Да или нет</span><span class="sxs-lookup"><span data-stu-id="82694-387">createprofile : yes or no</span></span>
* <span data-ttu-id="82694-388">ключ: общего ключа, hex64 кодировке</span><span class="sxs-lookup"><span data-stu-id="82694-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="82694-389">Средство записи производительности Windows</span><span class="sxs-lookup"><span data-stu-id="82694-389">Windows Performance Recorder</span></span>

<span data-ttu-id="82694-390">**/API/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="82694-391">Передает WPR профиль и запускает трассировку с помощью загруженного профиля.</span><span class="sxs-lookup"><span data-stu-id="82694-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="82694-392">полезные данные</span><span class="sxs-lookup"><span data-stu-id="82694-392">Payload</span></span>
* <span data-ttu-id="82694-393">составной согласование основного текста http</span><span class="sxs-lookup"><span data-stu-id="82694-393">multi-part conforming http body</span></span>

<span data-ttu-id="82694-394">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-394">Return data</span></span>
* <span data-ttu-id="82694-395">Возвращает состояние сеанса WPR.</span><span class="sxs-lookup"><span data-stu-id="82694-395">Returns the WPR session status.</span></span>

<span data-ttu-id="82694-396">**/API/wpr/Status (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="82694-397">Получает сведения о состоянии сеанса WPR</span><span class="sxs-lookup"><span data-stu-id="82694-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="82694-398">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-398">Return data</span></span>
* <span data-ttu-id="82694-399">Состояние сеанса в WPR.</span><span class="sxs-lookup"><span data-stu-id="82694-399">WPR session status.</span></span>

<span data-ttu-id="82694-400">**/API/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="82694-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="82694-401">Останавливает сеанс трассировки WPR (производительность)</span><span class="sxs-lookup"><span data-stu-id="82694-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="82694-402">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-402">Return data</span></span>
* <span data-ttu-id="82694-403">Возвращает ETL-файла трассировки</span><span class="sxs-lookup"><span data-stu-id="82694-403">Returns the trace ETL file</span></span>

<span data-ttu-id="82694-404">**/API/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="82694-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="82694-405">Запускает WPR (производительность), отслеживание сеансов</span><span class="sxs-lookup"><span data-stu-id="82694-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="82694-406">Параметры</span><span class="sxs-lookup"><span data-stu-id="82694-406">Parameters</span></span>
* <span data-ttu-id="82694-407">профиль: Имя профиля.</span><span class="sxs-lookup"><span data-stu-id="82694-407">profile : Profile name.</span></span> <span data-ttu-id="82694-408">Доступные профили хранятся в perfprofiles/profiles.json</span><span class="sxs-lookup"><span data-stu-id="82694-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="82694-409">Возвращаемые данные</span><span class="sxs-lookup"><span data-stu-id="82694-409">Return data</span></span>
* <span data-ttu-id="82694-410">При запуске возвращает состояние сеанса WPR.</span><span class="sxs-lookup"><span data-stu-id="82694-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="82694-411">См. также</span><span class="sxs-lookup"><span data-stu-id="82694-411">See also</span></span>
* [<span data-ttu-id="82694-412">С помощью Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="82694-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="82694-413">Core портала устройства Справочник по API (UWP)</span><span class="sxs-lookup"><span data-stu-id="82694-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
