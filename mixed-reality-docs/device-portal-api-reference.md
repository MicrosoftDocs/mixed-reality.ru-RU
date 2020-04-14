---
title: Справочник по API портала устройств
description: Справочник по API для портала устройств Windows на HoloLens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, портал устройств Windows, API
ms.openlocfilehash: 236de35c2c736fc5a0289b7be1f1548f0a08fa26
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278242"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="e32c9-104">Справочник по API портала устройств</span><span class="sxs-lookup"><span data-stu-id="e32c9-104">Device portal API reference</span></span>

<span data-ttu-id="e32c9-105">Все на [портале устройств Windows](using-the-windows-device-portal.md) основаны на REST API, которые можно использовать для программного доступа к данным и управления устройством.</span><span class="sxs-lookup"><span data-stu-id="e32c9-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="e32c9-106">Развертывании приложения</span><span class="sxs-lookup"><span data-stu-id="e32c9-106">App deloyment</span></span>

<span data-ttu-id="e32c9-107">**/АПИ/АПП/паккажеманажер/паккаже (удаление)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="e32c9-108">Удаляет приложение.</span><span class="sxs-lookup"><span data-stu-id="e32c9-108">Uninstalls an app</span></span>

<span data-ttu-id="e32c9-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-109">Parameters</span></span>
* <span data-ttu-id="e32c9-110">Пакет: имя файла удаляемого пакета.</span><span class="sxs-lookup"><span data-stu-id="e32c9-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="e32c9-111">**/АПИ/АПП/паккажеманажер/паккаже (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="e32c9-112">Устанавливает приложение</span><span class="sxs-lookup"><span data-stu-id="e32c9-112">Installs an App</span></span>

<span data-ttu-id="e32c9-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-113">Parameters</span></span>
* <span data-ttu-id="e32c9-114">Пакет: имя файла устанавливаемого пакета.</span><span class="sxs-lookup"><span data-stu-id="e32c9-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="e32c9-115">Payload</span><span class="sxs-lookup"><span data-stu-id="e32c9-115">Payload</span></span>
* <span data-ttu-id="e32c9-116">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="e32c9-116">multi-part conforming http body</span></span>

<span data-ttu-id="e32c9-117">**/АПИ/АПП/паккажеманажер/паккажес (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="e32c9-118">Извлекает список установленных приложений в системе со сведениями</span><span class="sxs-lookup"><span data-stu-id="e32c9-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="e32c9-119">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-119">Return data</span></span>
* <span data-ttu-id="e32c9-120">Список установленных пакетов со сведениями</span><span class="sxs-lookup"><span data-stu-id="e32c9-120">List of installed packages with details</span></span>

<span data-ttu-id="e32c9-121">**/АПИ/АПП/паккажеманажер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="e32c9-122">Возвращает состояние выполняющейся установки приложения.</span><span class="sxs-lookup"><span data-stu-id="e32c9-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="e32c9-123">Коллекция дампов</span><span class="sxs-lookup"><span data-stu-id="e32c9-123">Dump collection</span></span>

<span data-ttu-id="e32c9-124">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (удаление)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="e32c9-125">Отключает сбор аварийных дампов для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="e32c9-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="e32c9-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-126">Parameters</span></span>
* <span data-ttu-id="e32c9-127">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="e32c9-127">packageFullname : package name</span></span>

<span data-ttu-id="e32c9-128">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="e32c9-129">Получение параметров для коллекции аварийных дампов приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="e32c9-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="e32c9-130">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-130">Parameters</span></span>
* <span data-ttu-id="e32c9-131">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="e32c9-131">packageFullname : package name</span></span>

<span data-ttu-id="e32c9-132">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="e32c9-133">Включает и задает параметры управления дампом для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="e32c9-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="e32c9-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-134">Parameters</span></span>
* <span data-ttu-id="e32c9-135">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="e32c9-135">packageFullname : package name</span></span>

<span data-ttu-id="e32c9-136">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (удаление)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="e32c9-137">Удаляет аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="e32c9-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="e32c9-138">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-138">Parameters</span></span>
* <span data-ttu-id="e32c9-139">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="e32c9-139">packageFullname : package name</span></span>
* <span data-ttu-id="e32c9-140">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="e32c9-140">fileName : dump file name</span></span>

<span data-ttu-id="e32c9-141">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="e32c9-142">Получает аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="e32c9-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="e32c9-143">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-143">Parameters</span></span>
* <span data-ttu-id="e32c9-144">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="e32c9-144">packageFullname : package name</span></span>
* <span data-ttu-id="e32c9-145">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="e32c9-145">fileName : dump file name</span></span>

<span data-ttu-id="e32c9-146">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-146">Return data</span></span>
* <span data-ttu-id="e32c9-147">Файл дампа.</span><span class="sxs-lookup"><span data-stu-id="e32c9-147">Dump file.</span></span> <span data-ttu-id="e32c9-148">Проверка с помощью WinDbg или Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e32c9-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="e32c9-149">**/АПИ/дебуг/ДУМП/усермоде/думпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="e32c9-150">Возвращает список всех аварийных дампов для приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="e32c9-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="e32c9-151">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-151">Return data</span></span>
* <span data-ttu-id="e32c9-152">Список аварийных дампов для приложения, загруженного на стороне</span><span class="sxs-lookup"><span data-stu-id="e32c9-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="e32c9-153">трассировка событий Windows</span><span class="sxs-lookup"><span data-stu-id="e32c9-153">ETW</span></span>

<span data-ttu-id="e32c9-154">**/АПИ/ЕТВ/провидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="e32c9-155">Перечисляет зарегистрированные поставщики</span><span class="sxs-lookup"><span data-stu-id="e32c9-155">Enumerates registered providers</span></span>

<span data-ttu-id="e32c9-156">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-156">Return data</span></span>
* <span data-ttu-id="e32c9-157">Список поставщиков, понятное имя и идентификатор GUID</span><span class="sxs-lookup"><span data-stu-id="e32c9-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="e32c9-158">**/АПИ/ЕТВ/Сессион/реалтиме (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="e32c9-159">Создает сеанс ETW в режиме реального времени; управляется через WebSocket.</span><span class="sxs-lookup"><span data-stu-id="e32c9-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="e32c9-160">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-160">Return data</span></span>
* <span data-ttu-id="e32c9-161">События ETW из включенных поставщиков</span><span class="sxs-lookup"><span data-stu-id="e32c9-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="e32c9-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="e32c9-162">Holographic OS</span></span>

<span data-ttu-id="e32c9-163">**/АПИ/холографик/ОС/ЕТВ/кустомпровидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="e32c9-164">Возвращает список поставщиков ETW, которые не зарегистрированы в системе.</span><span class="sxs-lookup"><span data-stu-id="e32c9-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="e32c9-165">**/АПИ/холографик/ОС/сервицес (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="e32c9-166">Возвращает состояния всех служб, на которых выполняются службы.</span><span class="sxs-lookup"><span data-stu-id="e32c9-166">Returns the states of all services running.</span></span>

<span data-ttu-id="e32c9-167">**/АПИ/холографик/ОС/Сеттингс/ИПД (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="e32c9-168">Получает хранимую IPD (Интерпупиллари distance) в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="e32c9-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="e32c9-169">**/АПИ/холографик/ОС/Сеттингс/ИПД (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="e32c9-170">Задает IPD</span><span class="sxs-lookup"><span data-stu-id="e32c9-170">Sets the IPD</span></span>

<span data-ttu-id="e32c9-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-171">Parameters</span></span>
* <span data-ttu-id="e32c9-172">IPD: новое значение IPD для установки в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="e32c9-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="e32c9-173">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="e32c9-174">Получение требований HTTPS для Портала устройств</span><span class="sxs-lookup"><span data-stu-id="e32c9-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="e32c9-175">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="e32c9-176">Установка требований HTTPS для портала устройств</span><span class="sxs-lookup"><span data-stu-id="e32c9-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="e32c9-177">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-177">Parameters</span></span>
* <span data-ttu-id="e32c9-178">обязательный: Да, нет или по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e32c9-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="e32c9-179">Holographic восприятие</span><span class="sxs-lookup"><span data-stu-id="e32c9-179">Holographic Perception</span></span>

<span data-ttu-id="e32c9-180">**/АПИ/холографик/перцептион/клиент (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="e32c9-181">Принимает обновления WebSocket и запускает клиент-восприятие, которое отправляет обновления с частотой 30 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="e32c9-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="e32c9-182">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-182">Parameters</span></span>
* <span data-ttu-id="e32c9-183">клиентмоде: "Active" запускает режим отслеживания визуального элемента, если он не может быть установлен в пассивном режиме</span><span class="sxs-lookup"><span data-stu-id="e32c9-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="e32c9-184">Голограмма holographic</span><span class="sxs-lookup"><span data-stu-id="e32c9-184">Holographic Thermal</span></span>

<span data-ttu-id="e32c9-185">**/АПИ/холографик/сермал/стаже (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="e32c9-186">Получите температурный этап устройства (0 нормальная, 1 тепло, 2 критическая)</span><span class="sxs-lookup"><span data-stu-id="e32c9-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="e32c9-187">Элемент управления имитацией восприятия</span><span class="sxs-lookup"><span data-stu-id="e32c9-187">Perception Simulation Control</span></span>

<span data-ttu-id="e32c9-188">**/АПИ/холографик/симулатион/контрол/моде (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="e32c9-189">Получение режима имитации</span><span class="sxs-lookup"><span data-stu-id="e32c9-189">Get the simulation mode</span></span>

<span data-ttu-id="e32c9-190">**/АПИ/холографик/симулатион/контрол/моде (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="e32c9-191">Установка режима имитации</span><span class="sxs-lookup"><span data-stu-id="e32c9-191">Set the simulation mode</span></span>

<span data-ttu-id="e32c9-192">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-192">Parameters</span></span>
* <span data-ttu-id="e32c9-193">режим: режим имитации: по умолчанию, имитация, удаленный, устаревший</span><span class="sxs-lookup"><span data-stu-id="e32c9-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="e32c9-194">**/АПИ/холографик/симулатион/контрол/стреам (удаление)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="e32c9-195">Удаляет поток управления.</span><span class="sxs-lookup"><span data-stu-id="e32c9-195">Delete a control stream.</span></span>

<span data-ttu-id="e32c9-196">**/АПИ/холографик/симулатион/контрол/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="e32c9-197">Откройте подключение к веб-сокету для потока управления.</span><span class="sxs-lookup"><span data-stu-id="e32c9-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="e32c9-198">**/АПИ/холографик/симулатион/контрол/стреам (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="e32c9-199">Создайте поток управления (требуется приоритет) или опубликуйте данные в созданном потоке (требуется streamId).</span><span class="sxs-lookup"><span data-stu-id="e32c9-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="e32c9-200">Ожидаемые данные должны иметь тип "Application/октет-Stream".</span><span class="sxs-lookup"><span data-stu-id="e32c9-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="e32c9-201">Воспроизведение имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="e32c9-201">Perception Simulation Playback</span></span>

<span data-ttu-id="e32c9-202">**/АПИ/холографик/симулатион/плайбакк/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="e32c9-203">Удаление записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-203">Delete a recording.</span></span>

<span data-ttu-id="e32c9-204">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-204">Parameters</span></span>
* <span data-ttu-id="e32c9-205">запись: имя записи для удаления.</span><span class="sxs-lookup"><span data-stu-id="e32c9-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="e32c9-206">**/АПИ/холографик/симулатион/плайбакк/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="e32c9-207">Отправьте запись.</span><span class="sxs-lookup"><span data-stu-id="e32c9-207">Upload a recording.</span></span>

<span data-ttu-id="e32c9-208">**/АПИ/холографик/симулатион/плайбакк/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="e32c9-209">Получение всех записей.</span><span class="sxs-lookup"><span data-stu-id="e32c9-209">Get all recordings.</span></span>

<span data-ttu-id="e32c9-210">**/АПИ/холографик/симулатион/плайбакк/Сессион (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="e32c9-211">Получение текущего состояния воспроизведения записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="e32c9-212">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-212">Parameters</span></span>
* <span data-ttu-id="e32c9-213">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-213">recording : Name of recording.</span></span>

<span data-ttu-id="e32c9-214">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="e32c9-215">Выгрузить запись.</span><span class="sxs-lookup"><span data-stu-id="e32c9-215">Unload a recording.</span></span>

<span data-ttu-id="e32c9-216">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-216">Parameters</span></span>
* <span data-ttu-id="e32c9-217">запись: имя записи для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="e32c9-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="e32c9-218">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="e32c9-219">Загрузка записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-219">Load a recording.</span></span>

<span data-ttu-id="e32c9-220">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-220">Parameters</span></span>
* <span data-ttu-id="e32c9-221">запись: имя загружаемой записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="e32c9-222">**/АПИ/холографик/симулатион/плайбакк/Сессион/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="e32c9-223">Получение всех загруженных записей.</span><span class="sxs-lookup"><span data-stu-id="e32c9-223">Get all loaded recordings.</span></span>

<span data-ttu-id="e32c9-224">**/АПИ/холографик/симулатион/плайбакк/Сессион/паусе (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="e32c9-225">Приостановка записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-225">Pause a recording.</span></span>

<span data-ttu-id="e32c9-226">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-226">Parameters</span></span>
* <span data-ttu-id="e32c9-227">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-227">recording : Name of recording.</span></span>

<span data-ttu-id="e32c9-228">**/АПИ/холографик/симулатион/плайбакк/Сессион/Плай (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="e32c9-229">Воспроизведение записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-229">Play a recording.</span></span>

<span data-ttu-id="e32c9-230">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-230">Parameters</span></span>
* <span data-ttu-id="e32c9-231">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-231">recording : Name of recording.</span></span>

<span data-ttu-id="e32c9-232">**/АПИ/холографик/симулатион/плайбакк/Сессион/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="e32c9-233">Останавливает запись.</span><span class="sxs-lookup"><span data-stu-id="e32c9-233">Stop a recording.</span></span>

<span data-ttu-id="e32c9-234">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-234">Parameters</span></span>
* <span data-ttu-id="e32c9-235">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-235">recording : Name of recording.</span></span>

<span data-ttu-id="e32c9-236">**/АПИ/холографик/симулатион/плайбакк/Сессион/типес (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="e32c9-237">Получение типов данных в загруженной записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="e32c9-238">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-238">Parameters</span></span>
* <span data-ttu-id="e32c9-239">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="e32c9-240">Запись имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="e32c9-240">Perception Simulation Recording</span></span>

<span data-ttu-id="e32c9-241">**/АПИ/холографик/симулатион/рекординг/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="e32c9-242">Начать запись.</span><span class="sxs-lookup"><span data-stu-id="e32c9-242">Start a recording.</span></span> <span data-ttu-id="e32c9-243">Одновременно может быть активна только одна запись.</span><span class="sxs-lookup"><span data-stu-id="e32c9-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="e32c9-244">Необходимо задать один из головок, «руки», «Спатиалмаппинг» или «среда».</span><span class="sxs-lookup"><span data-stu-id="e32c9-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="e32c9-245">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-245">Parameters</span></span>
* <span data-ttu-id="e32c9-246">Head: задайте значение 1, чтобы записать данные заголовка.</span><span class="sxs-lookup"><span data-stu-id="e32c9-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="e32c9-247">стрелки: значение 1, чтобы записать данные.</span><span class="sxs-lookup"><span data-stu-id="e32c9-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="e32c9-248">Спатиалмаппинг: задайте значение 1 для записи пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="e32c9-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="e32c9-249">окружение: задайте значение 1, чтобы записать данные среды.</span><span class="sxs-lookup"><span data-stu-id="e32c9-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="e32c9-250">имя. имя записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-250">name : Name of the recording.</span></span>
* <span data-ttu-id="e32c9-251">Синглеспатиалмаппингфраме: задайте значение 1, чтобы записать только один фрейм пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="e32c9-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="e32c9-252">**/АПИ/холографик/симулатион/рекординг/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="e32c9-253">Получение состояния записи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-253">Get recording state.</span></span>

<span data-ttu-id="e32c9-254">**/АПИ/холографик/симулатион/рекординг/стоп (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="e32c9-255">Останавливает текущую запись.</span><span class="sxs-lookup"><span data-stu-id="e32c9-255">Stop the current recording.</span></span> <span data-ttu-id="e32c9-256">Запись будет возвращена в виде файла.</span><span class="sxs-lookup"><span data-stu-id="e32c9-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="e32c9-257">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="e32c9-257">Mixed Reality Capture</span></span>

<span data-ttu-id="e32c9-258">**/АПИ/холографик/МРК/филе (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="e32c9-259">Скачивает файл смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="e32c9-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="e32c9-260">Use Op = потоковый параметр запроса для потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="e32c9-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="e32c9-261">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-261">Parameters</span></span>
* <span data-ttu-id="e32c9-262">имя файла: имя, hex64 в кодировке для получаемого видео.</span><span class="sxs-lookup"><span data-stu-id="e32c9-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="e32c9-263">Op: Stream</span><span class="sxs-lookup"><span data-stu-id="e32c9-263">op : stream</span></span>

<span data-ttu-id="e32c9-264">**/АПИ/холографик/МРК/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="e32c9-265">Удаляет запись смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="e32c9-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="e32c9-266">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-266">Parameters</span></span>
* <span data-ttu-id="e32c9-267">filename: Name, hex64 Encoded (имя файла), которое нужно удалить.</span><span class="sxs-lookup"><span data-stu-id="e32c9-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="e32c9-268">**/АПИ/холографик/МРК/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="e32c9-269">Возвращает список файлов смешанной реальности, хранящихся на устройстве</span><span class="sxs-lookup"><span data-stu-id="e32c9-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="e32c9-270">**/АПИ/холографик/МРК/фото (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="e32c9-271">Принимает фотографию смешанной реальности и создает файл на устройстве</span><span class="sxs-lookup"><span data-stu-id="e32c9-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="e32c9-272">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-272">Parameters</span></span>
* <span data-ttu-id="e32c9-273">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="e32c9-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="e32c9-274">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="e32c9-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="e32c9-275">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="e32c9-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="e32c9-276">**/АПИ/холографик/МРК/Сеттингс (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="e32c9-277">Получает параметры записи смешанной реальности по умолчанию</span><span class="sxs-lookup"><span data-stu-id="e32c9-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="e32c9-278">**/АПИ/холографик/МРК/Сеттингс (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="e32c9-279">Задает параметры записи смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e32c9-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="e32c9-280">Некоторые из этих параметров применяются к фотографии и видеозаписи системы требований к системе.</span><span class="sxs-lookup"><span data-stu-id="e32c9-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="e32c9-281">**/АПИ/холографик/МРК/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="e32c9-282">Возвращает состояние записанной смешанной реальности (запущена, остановлена)</span><span class="sxs-lookup"><span data-stu-id="e32c9-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="e32c9-283">**/АПИ/холографик/МРК/сумбнаил (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="e32c9-284">Получает эскиз изображения для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="e32c9-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="e32c9-285">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-285">Parameters</span></span>
* <span data-ttu-id="e32c9-286">filename: Name, hex64 Encoded, файла, для которого запрашивается эскиз.</span><span class="sxs-lookup"><span data-stu-id="e32c9-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="e32c9-287">**/АПИ/холографик/МРК/видео/контрол/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="e32c9-288">Запуск записи смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="e32c9-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="e32c9-289">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-289">Parameters</span></span>
* <span data-ttu-id="e32c9-290">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="e32c9-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="e32c9-291">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="e32c9-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="e32c9-292">MIC: записать микрофон: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="e32c9-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="e32c9-293">замыкание на себя: запись звука приложения: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="e32c9-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="e32c9-294">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="e32c9-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="e32c9-295">встаб: (только HoloLens 2) Enable Video стабилизации: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="e32c9-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="e32c9-296">встаббуффер: (только HoloLens 2) задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="e32c9-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="e32c9-297">**/АПИ/холографик/МРК/видео/контрол/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="e32c9-298">Останавливает текущую запись смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="e32c9-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="e32c9-299">Потоковая передача смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="e32c9-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="e32c9-300">HoloLens поддерживает динамическую предварительную версию смешанной реальности через частную загрузку фрагментированного MP4.</span><span class="sxs-lookup"><span data-stu-id="e32c9-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="e32c9-301">Потоки смешанной реальности используют один и тот же набор параметров для управления тем, что захватывается:</span><span class="sxs-lookup"><span data-stu-id="e32c9-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="e32c9-302">Холо: голограммы записи: true или false</span><span class="sxs-lookup"><span data-stu-id="e32c9-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="e32c9-303">ПС: запись камеры PV: true или false</span><span class="sxs-lookup"><span data-stu-id="e32c9-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="e32c9-304">микрофон: записать микрофон: true или false</span><span class="sxs-lookup"><span data-stu-id="e32c9-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="e32c9-305">замыкание на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="e32c9-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="e32c9-306">Если ни один из этих элементов не указан: будут записываться голограммы, Фото-и видеокамера и звук приложения</span><span class="sxs-lookup"><span data-stu-id="e32c9-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="e32c9-307">Если таковые имеются, то по умолчанию для неуказанных параметров будет задано значение false.</span><span class="sxs-lookup"><span data-stu-id="e32c9-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="e32c9-308">Необязательные параметры (только HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="e32c9-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="e32c9-309">Рендерфромкамера: прорисовка с точки зрения фотографии или видеокамеры: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="e32c9-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="e32c9-310">встаб: enable Video стабилизации: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="e32c9-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="e32c9-311">встаббуффер: задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="e32c9-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="e32c9-312">**/API/holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="e32c9-313">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="e32c9-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="e32c9-314">**/АПИ/холографик/стреам/live_high. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="e32c9-315">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="e32c9-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="e32c9-316">**/АПИ/холографик/стреам/live_med. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="e32c9-317">Поток 854x480p 30fps 2.5 Мбит.</span><span class="sxs-lookup"><span data-stu-id="e32c9-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="e32c9-318">**/АПИ/холографик/стреам/live_low. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="e32c9-319">Поток 428x240p 15fps 0,6 Мбит.</span><span class="sxs-lookup"><span data-stu-id="e32c9-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="e32c9-320">Сеть</span><span class="sxs-lookup"><span data-stu-id="e32c9-320">Networking</span></span>

<span data-ttu-id="e32c9-321">**/АПИ/нетворкинг/ипконфиг (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="e32c9-322">Возвращает текущую IP-конфигурацию</span><span class="sxs-lookup"><span data-stu-id="e32c9-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="e32c9-323">Сведения о ОС</span><span class="sxs-lookup"><span data-stu-id="e32c9-323">OS Information</span></span>

<span data-ttu-id="e32c9-324">**/АПИ/ОС/Инфо (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="e32c9-325">Получение сведений об операционной системе</span><span class="sxs-lookup"><span data-stu-id="e32c9-325">Gets operating system information</span></span>

<span data-ttu-id="e32c9-326">**/АПИ/ОС/мачиненаме (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="e32c9-327">Возвращает имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="e32c9-327">Gets the machine name</span></span>

<span data-ttu-id="e32c9-328">**/АПИ/ОС/мачиненаме (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="e32c9-329">Задает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="e32c9-329">Sets the machine name</span></span>

<span data-ttu-id="e32c9-330">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-330">Parameters</span></span>
* <span data-ttu-id="e32c9-331">Имя: новое имя компьютера, hex64 в кодировке, для которого задано значение.</span><span class="sxs-lookup"><span data-stu-id="e32c9-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="e32c9-332">Данные о производительности</span><span class="sxs-lookup"><span data-stu-id="e32c9-332">Performance data</span></span>

<span data-ttu-id="e32c9-333">**/АПИ/ресаурцеманажер/процессес (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="e32c9-334">Возвращает список запущенных процессов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="e32c9-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="e32c9-335">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-335">Return data</span></span>
* <span data-ttu-id="e32c9-336">JSON со списком процессов и сведений для каждого процесса</span><span class="sxs-lookup"><span data-stu-id="e32c9-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="e32c9-337">**/АПИ/ресаурцеманажер/системперф (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="e32c9-338">Возвращает статистику производительности системы (операции чтения и записи ввода-вывода, статистика памяти и т. д.).</span><span class="sxs-lookup"><span data-stu-id="e32c9-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="e32c9-339">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-339">Return data</span></span>
* <span data-ttu-id="e32c9-340">JSON со сведениями о системе: ЦП, GPU, память, сеть, IO</span><span class="sxs-lookup"><span data-stu-id="e32c9-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="e32c9-341">Питание</span><span class="sxs-lookup"><span data-stu-id="e32c9-341">Power</span></span>

<span data-ttu-id="e32c9-342">**/АПИ/повер/Баттери (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="e32c9-343">Возвращает текущее состояние аккумулятора</span><span class="sxs-lookup"><span data-stu-id="e32c9-343">Gets the current battery state</span></span>

<span data-ttu-id="e32c9-344">**/АПИ/повер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="e32c9-345">Проверяет, находится ли система в состоянии с низким энергопотреблением</span><span class="sxs-lookup"><span data-stu-id="e32c9-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="e32c9-346">Выбор/Управление</span><span class="sxs-lookup"><span data-stu-id="e32c9-346">Remote Control</span></span>

<span data-ttu-id="e32c9-347">**/АПИ/контрол/рестарт (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="e32c9-348">Перезапускает целевое устройство</span><span class="sxs-lookup"><span data-stu-id="e32c9-348">Restarts the target device</span></span>

<span data-ttu-id="e32c9-349">**/АПИ/контрол/шутдовн (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="e32c9-350">Завершает работу целевого устройства</span><span class="sxs-lookup"><span data-stu-id="e32c9-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="e32c9-351">Диспетчер задач</span><span class="sxs-lookup"><span data-stu-id="e32c9-351">Task Manager</span></span>

<span data-ttu-id="e32c9-352">**/АПИ/таскманажер/АПП (удаление)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="e32c9-353">Останавливает современное приложение</span><span class="sxs-lookup"><span data-stu-id="e32c9-353">Stops a modern app</span></span>

<span data-ttu-id="e32c9-354">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-354">Parameters</span></span>
* <span data-ttu-id="e32c9-355">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="e32c9-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="e32c9-356">форцестоп: принудительно останавливаются все процессы (= да)</span><span class="sxs-lookup"><span data-stu-id="e32c9-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="e32c9-357">**/АПИ/таскманажер/АПП (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="e32c9-358">Запуск современного приложения</span><span class="sxs-lookup"><span data-stu-id="e32c9-358">Starts a modern app</span></span>

<span data-ttu-id="e32c9-359">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-359">Parameters</span></span>
* <span data-ttu-id="e32c9-360">AppID: ПРАИД приложения для запуска, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="e32c9-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="e32c9-361">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="e32c9-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="e32c9-362">Управление Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="e32c9-362">WiFi Management</span></span>

<span data-ttu-id="e32c9-363">**/АПИ/ВИФИ/интерфацес (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="e32c9-364">Перечисляет беспроводные сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="e32c9-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="e32c9-365">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-365">Return data</span></span>
* <span data-ttu-id="e32c9-366">Список беспроводных интерфейсов с подробными сведениями (GUID, описание и т. д.).</span><span class="sxs-lookup"><span data-stu-id="e32c9-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="e32c9-367">**/АПИ/ВИФИ/Нетворк (удаление)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="e32c9-368">Удаление профиля, связанного с сетью, в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="e32c9-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="e32c9-369">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-369">Parameters</span></span>
* <span data-ttu-id="e32c9-370">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="e32c9-370">interface : network interface guid</span></span>
* <span data-ttu-id="e32c9-371">Профиль: имя профиля</span><span class="sxs-lookup"><span data-stu-id="e32c9-371">profile : profile name</span></span>

<span data-ttu-id="e32c9-372">**/АПИ/ВИФИ/Нетворкс (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="e32c9-373">Перечисляет беспроводные сети в указанном сетевом интерфейсе</span><span class="sxs-lookup"><span data-stu-id="e32c9-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="e32c9-374">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-374">Parameters</span></span>
* <span data-ttu-id="e32c9-375">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="e32c9-375">interface : network interface guid</span></span>

<span data-ttu-id="e32c9-376">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-376">Return data</span></span>
* <span data-ttu-id="e32c9-377">Список беспроводных сетей, обнаруженных в сетевом интерфейсе, с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="e32c9-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="e32c9-378">**/АПИ/ВИФИ/Нетворк (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="e32c9-379">Подключение к сети или отключение от него по указанному интерфейсу</span><span class="sxs-lookup"><span data-stu-id="e32c9-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="e32c9-380">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-380">Parameters</span></span>
* <span data-ttu-id="e32c9-381">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="e32c9-381">interface : network interface guid</span></span>
* <span data-ttu-id="e32c9-382">SSID: SSID, hex64 в кодировке для подключения</span><span class="sxs-lookup"><span data-stu-id="e32c9-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="e32c9-383">Операция: подключение или отключение</span><span class="sxs-lookup"><span data-stu-id="e32c9-383">op : connect or disconnect</span></span>
* <span data-ttu-id="e32c9-384">креатепрофиле: Да или нет</span><span class="sxs-lookup"><span data-stu-id="e32c9-384">createprofile : yes or no</span></span>
* <span data-ttu-id="e32c9-385">ключ: Shared Key, hex64 Encoded</span><span class="sxs-lookup"><span data-stu-id="e32c9-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="e32c9-386">Средство записи производительности Windows</span><span class="sxs-lookup"><span data-stu-id="e32c9-386">Windows Performance Recorder</span></span>

<span data-ttu-id="e32c9-387">**/АПИ/ВПР/кустомтраце (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="e32c9-388">Отправляет профиль ЗВЧ и начинает трассировку с помощью отправленного профиля.</span><span class="sxs-lookup"><span data-stu-id="e32c9-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="e32c9-389">Payload</span><span class="sxs-lookup"><span data-stu-id="e32c9-389">Payload</span></span>
* <span data-ttu-id="e32c9-390">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="e32c9-390">multi-part conforming http body</span></span>

<span data-ttu-id="e32c9-391">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-391">Return data</span></span>
* <span data-ttu-id="e32c9-392">Возвращает состояние сеанса WPR.</span><span class="sxs-lookup"><span data-stu-id="e32c9-392">Returns the WPR session status.</span></span>

<span data-ttu-id="e32c9-393">**/АПИ/ВПР/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="e32c9-394">Получение состояния сеанса ЗВЧ</span><span class="sxs-lookup"><span data-stu-id="e32c9-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="e32c9-395">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-395">Return data</span></span>
* <span data-ttu-id="e32c9-396">Состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="e32c9-396">WPR session status.</span></span>

<span data-ttu-id="e32c9-397">**/АПИ/ВПР/траце (GET)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="e32c9-398">Останавливает сеанс трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="e32c9-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="e32c9-399">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-399">Return data</span></span>
* <span data-ttu-id="e32c9-400">Возвращает ETL-файл трассировки</span><span class="sxs-lookup"><span data-stu-id="e32c9-400">Returns the trace ETL file</span></span>

<span data-ttu-id="e32c9-401">**/АПИ/ВПР/траце (POST)**</span><span class="sxs-lookup"><span data-stu-id="e32c9-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="e32c9-402">Запускает сеансы трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="e32c9-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="e32c9-403">Параметры</span><span class="sxs-lookup"><span data-stu-id="e32c9-403">Parameters</span></span>
* <span data-ttu-id="e32c9-404">Профиль: имя профиля.</span><span class="sxs-lookup"><span data-stu-id="e32c9-404">profile : Profile name.</span></span> <span data-ttu-id="e32c9-405">Доступные профили хранятся в перфпрофилес/Profiles. JSON.</span><span class="sxs-lookup"><span data-stu-id="e32c9-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="e32c9-406">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="e32c9-406">Return data</span></span>
* <span data-ttu-id="e32c9-407">При запуске возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="e32c9-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="e32c9-408">См. также:</span><span class="sxs-lookup"><span data-stu-id="e32c9-408">See also</span></span>
* [<span data-ttu-id="e32c9-409">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="e32c9-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="e32c9-410">Справочник по API для базовых порталов устройств (UWP)</span><span class="sxs-lookup"><span data-stu-id="e32c9-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
