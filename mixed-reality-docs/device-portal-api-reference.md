---
title: Справочник по API портала устройств
description: Справочник по API для портала устройств Windows на HoloLens
author: JonMLyons
ms.author: JLyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, портал устройств Windows, API
ms.openlocfilehash: 4b5b48c13b1b7ec8bfdf447f42097a8448b6a0e6
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694437"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="b0c61-104">Справочник по API портала устройств</span><span class="sxs-lookup"><span data-stu-id="b0c61-104">Device portal API reference</span></span>

<span data-ttu-id="b0c61-105">Все на [портале устройств Windows](using-the-windows-device-portal.md) основаны на REST API, которые можно использовать для программного доступа к данным и управления устройством.</span><span class="sxs-lookup"><span data-stu-id="b0c61-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="b0c61-106">Развертывании приложения</span><span class="sxs-lookup"><span data-stu-id="b0c61-106">App deloyment</span></span>

<span data-ttu-id="b0c61-107">**/АПИ/АПП/паккажеманажер/паккаже (удаление)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="b0c61-108">Удаляет приложение.</span><span class="sxs-lookup"><span data-stu-id="b0c61-108">Uninstalls an app</span></span>

<span data-ttu-id="b0c61-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-109">Parameters</span></span>
* <span data-ttu-id="b0c61-110">пакеты Имя файла удаляемого пакета.</span><span class="sxs-lookup"><span data-stu-id="b0c61-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="b0c61-111">**/АПИ/АПП/паккажеманажер/паккаже (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="b0c61-112">Устанавливает приложение</span><span class="sxs-lookup"><span data-stu-id="b0c61-112">Installs an App</span></span>

<span data-ttu-id="b0c61-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-113">Parameters</span></span>
* <span data-ttu-id="b0c61-114">пакеты Имя файла устанавливаемого пакета.</span><span class="sxs-lookup"><span data-stu-id="b0c61-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="b0c61-115">Полезных данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-115">Payload</span></span>
* <span data-ttu-id="b0c61-116">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="b0c61-116">multi-part conforming http body</span></span>

<span data-ttu-id="b0c61-117">**/АПИ/АПП/паккажеманажер/паккажес (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="b0c61-118">Извлекает список установленных приложений в системе со сведениями</span><span class="sxs-lookup"><span data-stu-id="b0c61-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="b0c61-119">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-119">Return data</span></span>
* <span data-ttu-id="b0c61-120">Список установленных пакетов со сведениями</span><span class="sxs-lookup"><span data-stu-id="b0c61-120">List of installed packages with details</span></span>

<span data-ttu-id="b0c61-121">**/АПИ/АПП/паккажеманажер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="b0c61-122">Возвращает состояние выполняющейся установки приложения.</span><span class="sxs-lookup"><span data-stu-id="b0c61-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="b0c61-123">Коллекция дампов</span><span class="sxs-lookup"><span data-stu-id="b0c61-123">Dump collection</span></span>

<span data-ttu-id="b0c61-124">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (удаление)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="b0c61-125">Отключает сбор аварийных дампов для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="b0c61-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="b0c61-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-126">Parameters</span></span>
* <span data-ttu-id="b0c61-127">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="b0c61-127">packageFullname : package name</span></span>

<span data-ttu-id="b0c61-128">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="b0c61-129">Получение параметров для коллекции аварийных дампов приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="b0c61-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="b0c61-130">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-130">Parameters</span></span>
* <span data-ttu-id="b0c61-131">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="b0c61-131">packageFullname : package name</span></span>

<span data-ttu-id="b0c61-132">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="b0c61-133">Включает и задает параметры управления дампом для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="b0c61-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="b0c61-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-134">Parameters</span></span>
* <span data-ttu-id="b0c61-135">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="b0c61-135">packageFullname : package name</span></span>

<span data-ttu-id="b0c61-136">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (удаление)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="b0c61-137">Удаляет аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="b0c61-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="b0c61-138">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-138">Parameters</span></span>
* <span data-ttu-id="b0c61-139">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="b0c61-139">packageFullname : package name</span></span>
* <span data-ttu-id="b0c61-140">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="b0c61-140">fileName : dump file name</span></span>

<span data-ttu-id="b0c61-141">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="b0c61-142">Получает аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="b0c61-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="b0c61-143">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-143">Parameters</span></span>
* <span data-ttu-id="b0c61-144">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="b0c61-144">packageFullname : package name</span></span>
* <span data-ttu-id="b0c61-145">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="b0c61-145">fileName : dump file name</span></span>

<span data-ttu-id="b0c61-146">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-146">Return data</span></span>
* <span data-ttu-id="b0c61-147">Файл дампа.</span><span class="sxs-lookup"><span data-stu-id="b0c61-147">Dump file.</span></span> <span data-ttu-id="b0c61-148">Проверка с помощью WinDbg или Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b0c61-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="b0c61-149">**/АПИ/дебуг/ДУМП/усермоде/думпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="b0c61-150">Возвращает список всех аварийных дампов для приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="b0c61-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="b0c61-151">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-151">Return data</span></span>
* <span data-ttu-id="b0c61-152">Список аварийных дампов для приложения, загруженного на стороне</span><span class="sxs-lookup"><span data-stu-id="b0c61-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="b0c61-153">Трассировка событий Windows</span><span class="sxs-lookup"><span data-stu-id="b0c61-153">ETW</span></span>

<span data-ttu-id="b0c61-154">**/АПИ/ЕТВ/провидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="b0c61-155">Перечисляет зарегистрированные поставщики</span><span class="sxs-lookup"><span data-stu-id="b0c61-155">Enumerates registered providers</span></span>

<span data-ttu-id="b0c61-156">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-156">Return data</span></span>
* <span data-ttu-id="b0c61-157">Список поставщиков, понятное имя и идентификатор GUID</span><span class="sxs-lookup"><span data-stu-id="b0c61-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="b0c61-158">**/АПИ/ЕТВ/Сессион/реалтиме (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="b0c61-159">Создает сеанс ETW в режиме реального времени; управляется через WebSocket.</span><span class="sxs-lookup"><span data-stu-id="b0c61-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="b0c61-160">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-160">Return data</span></span>
* <span data-ttu-id="b0c61-161">События ETW из включенных поставщиков</span><span class="sxs-lookup"><span data-stu-id="b0c61-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="b0c61-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="b0c61-162">Holographic OS</span></span>

<span data-ttu-id="b0c61-163">**/АПИ/холографик/ОС/ЕТВ/кустомпровидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="b0c61-164">Возвращает список поставщиков ETW, которые не зарегистрированы в системе.</span><span class="sxs-lookup"><span data-stu-id="b0c61-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="b0c61-165">**/АПИ/холографик/ОС/сервицес (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="b0c61-166">Возвращает состояния всех служб, на которых выполняются службы.</span><span class="sxs-lookup"><span data-stu-id="b0c61-166">Returns the states of all services running.</span></span>

<span data-ttu-id="b0c61-167">**/АПИ/холографик/ОС/Сеттингс/ИПД (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="b0c61-168">Получает хранимую IPD (Интерпупиллари distance) в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="b0c61-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="b0c61-169">**/АПИ/холографик/ОС/Сеттингс/ИПД (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="b0c61-170">Задает IPD</span><span class="sxs-lookup"><span data-stu-id="b0c61-170">Sets the IPD</span></span>

<span data-ttu-id="b0c61-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-171">Parameters</span></span>
* <span data-ttu-id="b0c61-172">IPD Новое значение IPD для установки в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="b0c61-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="b0c61-173">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="b0c61-174">Получение требований HTTPS для Портала устройств</span><span class="sxs-lookup"><span data-stu-id="b0c61-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="b0c61-175">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="b0c61-176">Установка требований HTTPS для портала устройств</span><span class="sxs-lookup"><span data-stu-id="b0c61-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="b0c61-177">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-177">Parameters</span></span>
* <span data-ttu-id="b0c61-178">обязательный: Да, нет или по умолчанию</span><span class="sxs-lookup"><span data-stu-id="b0c61-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="b0c61-179">Holographic восприятие</span><span class="sxs-lookup"><span data-stu-id="b0c61-179">Holographic Perception</span></span>

<span data-ttu-id="b0c61-180">**/АПИ/холографик/перцептион/клиент (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="b0c61-181">Принимает обновления WebSocket и запускает клиент-восприятие, которое отправляет обновления с частотой 30 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="b0c61-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="b0c61-182">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-182">Parameters</span></span>
* <span data-ttu-id="b0c61-183">клиентмоде: "Active" запускает режим отслеживания визуального элемента, если он не может быть установлен в пассивном режиме</span><span class="sxs-lookup"><span data-stu-id="b0c61-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="b0c61-184">Голограмма holographic</span><span class="sxs-lookup"><span data-stu-id="b0c61-184">Holographic Thermal</span></span>

<span data-ttu-id="b0c61-185">**/АПИ/холографик/сермал/стаже (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="b0c61-186">Получите температурный этап устройства (0 нормальная, 1 тепло, 2 критическая)</span><span class="sxs-lookup"><span data-stu-id="b0c61-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="b0c61-187">Элемент управления имитацией восприятия</span><span class="sxs-lookup"><span data-stu-id="b0c61-187">Perception Simulation Control</span></span>

<span data-ttu-id="b0c61-188">**/АПИ/холографик/симулатион/контрол/моде (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="b0c61-189">Получение режима моделирования</span><span class="sxs-lookup"><span data-stu-id="b0c61-189">Get the simulation mode</span></span>

<span data-ttu-id="b0c61-190">**/АПИ/холографик/симулатион/контрол/моде (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="b0c61-191">Установка режима имитации</span><span class="sxs-lookup"><span data-stu-id="b0c61-191">Set the simulation mode</span></span>

<span data-ttu-id="b0c61-192">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-192">Parameters</span></span>
* <span data-ttu-id="b0c61-193">режим: режим имитации: по умолчанию, имитация, удаленный, устаревший</span><span class="sxs-lookup"><span data-stu-id="b0c61-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="b0c61-194">**/АПИ/холографик/симулатион/контрол/стреам (удаление)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="b0c61-195">Удаляет поток управления.</span><span class="sxs-lookup"><span data-stu-id="b0c61-195">Delete a control stream.</span></span>

<span data-ttu-id="b0c61-196">**/АПИ/холографик/симулатион/контрол/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="b0c61-197">Откройте подключение к веб-сокету для потока управления.</span><span class="sxs-lookup"><span data-stu-id="b0c61-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="b0c61-198">**/АПИ/холографик/симулатион/контрол/стреам (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="b0c61-199">Создайте поток управления (требуется приоритет) или опубликуйте данные в созданном потоке (требуется streamId).</span><span class="sxs-lookup"><span data-stu-id="b0c61-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="b0c61-200">Ожидаемые данные должны иметь тип "Application/октет-Stream".</span><span class="sxs-lookup"><span data-stu-id="b0c61-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="b0c61-201">Воспроизведение имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="b0c61-201">Perception Simulation Playback</span></span>

<span data-ttu-id="b0c61-202">**/АПИ/холографик/симулатион/плайбакк/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-202">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="b0c61-203">Удаление записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-203">Delete a recording.</span></span>

<span data-ttu-id="b0c61-204">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-204">Parameters</span></span>
* <span data-ttu-id="b0c61-205">запись Имя записи для удаления.</span><span class="sxs-lookup"><span data-stu-id="b0c61-205">recording : Name of recording to delete.</span></span>

<span data-ttu-id="b0c61-206">**/АПИ/холографик/симулатион/плайбакк/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-206">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="b0c61-207">Отправьте запись.</span><span class="sxs-lookup"><span data-stu-id="b0c61-207">Upload a recording.</span></span>

<span data-ttu-id="b0c61-208">**/АПИ/холографик/симулатион/плайбакк/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-208">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="b0c61-209">Получение всех записей.</span><span class="sxs-lookup"><span data-stu-id="b0c61-209">Get all recordings.</span></span>

<span data-ttu-id="b0c61-210">**/АПИ/холографик/симулатион/плайбакк/Сессион (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-210">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="b0c61-211">Получение текущего состояния воспроизведения записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-211">Get the current playback state of a recording.</span></span>

<span data-ttu-id="b0c61-212">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-212">Parameters</span></span>
* <span data-ttu-id="b0c61-213">запись Имя записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-213">recording : Name of recording.</span></span>

<span data-ttu-id="b0c61-214">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-214">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="b0c61-215">Выгрузить запись.</span><span class="sxs-lookup"><span data-stu-id="b0c61-215">Unload a recording.</span></span>

<span data-ttu-id="b0c61-216">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-216">Parameters</span></span>
* <span data-ttu-id="b0c61-217">запись Имя записи для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="b0c61-217">recording : Name of recording to unload.</span></span>

<span data-ttu-id="b0c61-218">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-218">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="b0c61-219">Загрузка записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-219">Load a recording.</span></span>

<span data-ttu-id="b0c61-220">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-220">Parameters</span></span>
* <span data-ttu-id="b0c61-221">запись Имя загружаемой записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-221">recording : Name of recording to load.</span></span>

<span data-ttu-id="b0c61-222">**/АПИ/холографик/симулатион/плайбакк/Сессион/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-222">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="b0c61-223">Получение всех загруженных записей.</span><span class="sxs-lookup"><span data-stu-id="b0c61-223">Get all loaded recordings.</span></span>

<span data-ttu-id="b0c61-224">**/АПИ/холографик/симулатион/плайбакк/Сессион/паусе (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-224">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="b0c61-225">Приостановка записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-225">Pause a recording.</span></span>

<span data-ttu-id="b0c61-226">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-226">Parameters</span></span>
* <span data-ttu-id="b0c61-227">запись Имя записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-227">recording : Name of recording.</span></span>

<span data-ttu-id="b0c61-228">**/АПИ/холографик/симулатион/плайбакк/Сессион/Плай (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-228">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="b0c61-229">Воспроизведение записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-229">Play a recording.</span></span>

<span data-ttu-id="b0c61-230">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-230">Parameters</span></span>
* <span data-ttu-id="b0c61-231">запись Имя записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-231">recording : Name of recording.</span></span>

<span data-ttu-id="b0c61-232">**/АПИ/холографик/симулатион/плайбакк/Сессион/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-232">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="b0c61-233">Останавливает запись.</span><span class="sxs-lookup"><span data-stu-id="b0c61-233">Stop a recording.</span></span>

<span data-ttu-id="b0c61-234">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-234">Parameters</span></span>
* <span data-ttu-id="b0c61-235">запись Имя записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-235">recording : Name of recording.</span></span>

<span data-ttu-id="b0c61-236">**/АПИ/холографик/симулатион/плайбакк/Сессион/типес (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-236">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="b0c61-237">Получение типов данных в загруженной записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-237">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="b0c61-238">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-238">Parameters</span></span>
* <span data-ttu-id="b0c61-239">запись Имя записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-239">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="b0c61-240">Запись имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="b0c61-240">Perception Simulation Recording</span></span>

<span data-ttu-id="b0c61-241">**/АПИ/холографик/симулатион/рекординг/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-241">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="b0c61-242">Начать запись.</span><span class="sxs-lookup"><span data-stu-id="b0c61-242">Start a recording.</span></span> <span data-ttu-id="b0c61-243">Одновременно может быть активна только одна запись.</span><span class="sxs-lookup"><span data-stu-id="b0c61-243">Only a single recording can be active at once.</span></span> <span data-ttu-id="b0c61-244">Необходимо задать один из головок, «руки», «Спатиалмаппинг» или «среда».</span><span class="sxs-lookup"><span data-stu-id="b0c61-244">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="b0c61-245">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-245">Parameters</span></span>
* <span data-ttu-id="b0c61-246">Глава Задайте значение 1, чтобы записать данные заголовка.</span><span class="sxs-lookup"><span data-stu-id="b0c61-246">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="b0c61-247">стрелки Задайте значение 1, чтобы записать данные в руки.</span><span class="sxs-lookup"><span data-stu-id="b0c61-247">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="b0c61-248">Спатиалмаппинг: Задайте значение 1 для записи пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="b0c61-248">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="b0c61-249">PXE Задайте значение 1, чтобы записать данные среды.</span><span class="sxs-lookup"><span data-stu-id="b0c61-249">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="b0c61-250">безымян Имя записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-250">name : Name of the recording.</span></span>
* <span data-ttu-id="b0c61-251">Синглеспатиалмаппингфраме: Задайте значение 1, чтобы записать только один фрейм пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="b0c61-251">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="b0c61-252">**/АПИ/холографик/симулатион/рекординг/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-252">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="b0c61-253">Получение состояния записи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-253">Get recording state.</span></span>

<span data-ttu-id="b0c61-254">**/АПИ/холографик/симулатион/рекординг/стоп (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-254">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="b0c61-255">Останавливает текущую запись.</span><span class="sxs-lookup"><span data-stu-id="b0c61-255">Stop the current recording.</span></span> <span data-ttu-id="b0c61-256">Запись будет возвращена в виде файла.</span><span class="sxs-lookup"><span data-stu-id="b0c61-256">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="b0c61-257">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="b0c61-257">Mixed Reality Capture</span></span>

<span data-ttu-id="b0c61-258">**/АПИ/холографик/МРК/филе (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="b0c61-259">Скачивает файл смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="b0c61-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="b0c61-260">Use Op = потоковый параметр запроса для потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="b0c61-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="b0c61-261">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-261">Parameters</span></span>
* <span data-ttu-id="b0c61-262">файлов Имя, hex64 в кодировке для получаемого видеофайла</span><span class="sxs-lookup"><span data-stu-id="b0c61-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="b0c61-263">Op: Stream</span><span class="sxs-lookup"><span data-stu-id="b0c61-263">op : stream</span></span>

<span data-ttu-id="b0c61-264">**/АПИ/холографик/МРК/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="b0c61-265">Удаляет запись смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="b0c61-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="b0c61-266">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-266">Parameters</span></span>
* <span data-ttu-id="b0c61-267">файлов Name, hex64 в кодировке, удаляемый файл</span><span class="sxs-lookup"><span data-stu-id="b0c61-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="b0c61-268">**/АПИ/холографик/МРК/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="b0c61-269">Возвращает список файлов смешанной реальности, хранящихся на устройстве</span><span class="sxs-lookup"><span data-stu-id="b0c61-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="b0c61-270">**/АПИ/холографик/МРК/фото (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="b0c61-271">Принимает фотографию смешанной реальности и создает файл на устройстве</span><span class="sxs-lookup"><span data-stu-id="b0c61-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="b0c61-272">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-272">Parameters</span></span>
* <span data-ttu-id="b0c61-273">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="b0c61-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="b0c61-274">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="b0c61-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="b0c61-275">Рендерфромкамера: (Только HoloLens 2) визуализация с точки зрения фотографии или видеокамеры: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="b0c61-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="b0c61-276">**/АПИ/холографик/МРК/Сеттингс (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="b0c61-277">Получает параметры записи смешанной реальности по умолчанию</span><span class="sxs-lookup"><span data-stu-id="b0c61-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="b0c61-278">**/АПИ/холографик/МРК/Сеттингс (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="b0c61-279">Задает параметры записи смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b0c61-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="b0c61-280">Некоторые из этих параметров применяются к фотографии и видеозаписи системы требований к системе.</span><span class="sxs-lookup"><span data-stu-id="b0c61-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="b0c61-281">**/АПИ/холографик/МРК/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="b0c61-282">Возвращает состояние записанной смешанной реальности (запущена, остановлена)</span><span class="sxs-lookup"><span data-stu-id="b0c61-282">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="b0c61-283">**/АПИ/холографик/МРК/сумбнаил (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-283">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="b0c61-284">Получает эскиз изображения для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="b0c61-284">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="b0c61-285">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-285">Parameters</span></span>
* <span data-ttu-id="b0c61-286">файлов Name (hex64 Encoded) файла, для которого запрашивается эскиз</span><span class="sxs-lookup"><span data-stu-id="b0c61-286">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="b0c61-287">**/АПИ/холографик/МРК/видео/контрол/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-287">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="b0c61-288">Запуск записи смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="b0c61-288">Starts a mixed reality recording</span></span>

<span data-ttu-id="b0c61-289">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-289">Parameters</span></span>
* <span data-ttu-id="b0c61-290">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="b0c61-290">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="b0c61-291">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="b0c61-291">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="b0c61-292">MIC: записать микрофон: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="b0c61-292">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="b0c61-293">замыкание на себя: запись звука приложения: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="b0c61-293">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="b0c61-294">Рендерфромкамера: (Только HoloLens 2) визуализация с точки зрения фотографии или видеокамеры: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="b0c61-294">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="b0c61-295">встаб: (Только HoloLens 2) включить видео стабилизации: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="b0c61-295">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="b0c61-296">встаббуффер: (Только HoloLens 2) задержка буфера видео стабилизации: от 0 до 30 кадров (по умолчанию — 15)</span><span class="sxs-lookup"><span data-stu-id="b0c61-296">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="b0c61-297">**/АПИ/холографик/МРК/видео/контрол/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-297">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="b0c61-298">Останавливает текущую запись смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="b0c61-298">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="b0c61-299">Потоковая передача смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="b0c61-299">Mixed Reality Streaming</span></span>

<span data-ttu-id="b0c61-300">HoloLens поддерживает динамическую предварительную версию смешанной реальности через частную загрузку фрагментированного MP4.</span><span class="sxs-lookup"><span data-stu-id="b0c61-300">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="b0c61-301">Потоки смешанной реальности используют один и тот же набор параметров для управления тем, что захватывается:</span><span class="sxs-lookup"><span data-stu-id="b0c61-301">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="b0c61-302">Холо: голограммы записи: true или false</span><span class="sxs-lookup"><span data-stu-id="b0c61-302">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="b0c61-303">ПС: запись камеры PV: true или false</span><span class="sxs-lookup"><span data-stu-id="b0c61-303">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="b0c61-304">микрофон: записать микрофон: true или false</span><span class="sxs-lookup"><span data-stu-id="b0c61-304">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="b0c61-305">замыкание на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="b0c61-305">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="b0c61-306">Если ни один из этих элементов не указан: будут записываться голограммы, Фото-и видеокамера и звук приложения</span><span class="sxs-lookup"><span data-stu-id="b0c61-306">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="b0c61-307">Если таковые имеются, то по умолчанию для неуказанных параметров будет задано значение false.</span><span class="sxs-lookup"><span data-stu-id="b0c61-307">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="b0c61-308">Необязательные параметры (только HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="b0c61-308">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="b0c61-309">Рендерфромкамера: прорисовка с точки зрения фотографии или видеокамеры: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="b0c61-309">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="b0c61-310">встаб: enable Video стабилизации: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="b0c61-310">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="b0c61-311">встаббуффер: задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15)</span><span class="sxs-lookup"><span data-stu-id="b0c61-311">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="b0c61-312">**/API/holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-312">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="b0c61-313">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="b0c61-313">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="b0c61-314">**/API/holographic/Stream/live_high.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-314">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="b0c61-315">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="b0c61-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="b0c61-316">**/API/holographic/Stream/live_med.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-316">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="b0c61-317">Поток 854x480p 30fps 2.5 Мбит.</span><span class="sxs-lookup"><span data-stu-id="b0c61-317">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="b0c61-318">**/API/holographic/Stream/live_low.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-318">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="b0c61-319">Поток 428x240p 15fps 0,6 Мбит.</span><span class="sxs-lookup"><span data-stu-id="b0c61-319">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="b0c61-320">Сеть</span><span class="sxs-lookup"><span data-stu-id="b0c61-320">Networking</span></span>

<span data-ttu-id="b0c61-321">**/АПИ/нетворкинг/ипконфиг (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-321">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="b0c61-322">Возвращает текущую IP-конфигурацию</span><span class="sxs-lookup"><span data-stu-id="b0c61-322">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="b0c61-323">Сведения о ОС</span><span class="sxs-lookup"><span data-stu-id="b0c61-323">OS Information</span></span>

<span data-ttu-id="b0c61-324">**/АПИ/ОС/Инфо (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-324">**/api/os/info (GET)**</span></span>

<span data-ttu-id="b0c61-325">Получение сведений об операционной системе</span><span class="sxs-lookup"><span data-stu-id="b0c61-325">Gets operating system information</span></span>

<span data-ttu-id="b0c61-326">**/АПИ/ОС/мачиненаме (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-326">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="b0c61-327">Возвращает имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="b0c61-327">Gets the machine name</span></span>

<span data-ttu-id="b0c61-328">**/АПИ/ОС/мачиненаме (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-328">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="b0c61-329">Задает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="b0c61-329">Sets the machine name</span></span>

<span data-ttu-id="b0c61-330">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-330">Parameters</span></span>
* <span data-ttu-id="b0c61-331">безымян Новое имя компьютера, hex64 в кодировке, для установки значения</span><span class="sxs-lookup"><span data-stu-id="b0c61-331">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="b0c61-332">Данные о производительности</span><span class="sxs-lookup"><span data-stu-id="b0c61-332">Performance data</span></span>

<span data-ttu-id="b0c61-333">**/АПИ/ресаурцеманажер/процессес (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-333">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="b0c61-334">Возвращает список запущенных процессов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="b0c61-334">Returns the list of running processes with details</span></span>

<span data-ttu-id="b0c61-335">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-335">Return data</span></span>
* <span data-ttu-id="b0c61-336">JSON со списком процессов и сведений для каждого процесса</span><span class="sxs-lookup"><span data-stu-id="b0c61-336">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="b0c61-337">**/АПИ/ресаурцеманажер/системперф (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-337">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="b0c61-338">Возвращает статистику производительности системы (операции чтения и записи ввода-вывода, статистика памяти и т. д.).</span><span class="sxs-lookup"><span data-stu-id="b0c61-338">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="b0c61-339">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-339">Return data</span></span>
* <span data-ttu-id="b0c61-340">JSON со сведениями о системе: ЦП, GPU, память, сеть, IO</span><span class="sxs-lookup"><span data-stu-id="b0c61-340">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="b0c61-341">Питание</span><span class="sxs-lookup"><span data-stu-id="b0c61-341">Power</span></span>

<span data-ttu-id="b0c61-342">**/АПИ/повер/Баттери (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-342">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="b0c61-343">Возвращает текущее состояние аккумулятора</span><span class="sxs-lookup"><span data-stu-id="b0c61-343">Gets the current battery state</span></span>

<span data-ttu-id="b0c61-344">**/АПИ/повер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-344">**/api/power/state (GET)**</span></span>

<span data-ttu-id="b0c61-345">Проверяет, находится ли система в состоянии с низким энергопотреблением</span><span class="sxs-lookup"><span data-stu-id="b0c61-345">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="b0c61-346">Удаленное управление</span><span class="sxs-lookup"><span data-stu-id="b0c61-346">Remote Control</span></span>

<span data-ttu-id="b0c61-347">**/АПИ/контрол/рестарт (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-347">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="b0c61-348">Перезапускает целевое устройство</span><span class="sxs-lookup"><span data-stu-id="b0c61-348">Restarts the target device</span></span>

<span data-ttu-id="b0c61-349">**/АПИ/контрол/шутдовн (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-349">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="b0c61-350">Завершает работу целевого устройства</span><span class="sxs-lookup"><span data-stu-id="b0c61-350">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="b0c61-351">Диспетчер задач</span><span class="sxs-lookup"><span data-stu-id="b0c61-351">Task Manager</span></span>

<span data-ttu-id="b0c61-352">**/АПИ/таскманажер/АПП (удаление)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-352">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="b0c61-353">Останавливает современное приложение</span><span class="sxs-lookup"><span data-stu-id="b0c61-353">Stops a modern app</span></span>

<span data-ttu-id="b0c61-354">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-354">Parameters</span></span>
* <span data-ttu-id="b0c61-355">пакеты Полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="b0c61-355">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="b0c61-356">форцестоп: Принудительно останавливаются все процессы (= да)</span><span class="sxs-lookup"><span data-stu-id="b0c61-356">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="b0c61-357">**/АПИ/таскманажер/АПП (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-357">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="b0c61-358">Запуск современного приложения</span><span class="sxs-lookup"><span data-stu-id="b0c61-358">Starts a modern app</span></span>

<span data-ttu-id="b0c61-359">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-359">Parameters</span></span>
* <span data-ttu-id="b0c61-360">ИД ПРАИД приложения для запуска, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="b0c61-360">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="b0c61-361">пакеты Полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="b0c61-361">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="b0c61-362">Управление Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="b0c61-362">WiFi Management</span></span>

<span data-ttu-id="b0c61-363">**/АПИ/ВИФИ/интерфацес (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-363">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="b0c61-364">Перечисляет беспроводные сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="b0c61-364">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="b0c61-365">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-365">Return data</span></span>
* <span data-ttu-id="b0c61-366">Список беспроводных интерфейсов с подробными сведениями (GUID, описание и т. д.).</span><span class="sxs-lookup"><span data-stu-id="b0c61-366">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="b0c61-367">**/АПИ/ВИФИ/Нетворк (удаление)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-367">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="b0c61-368">Удаление профиля, связанного с сетью, в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="b0c61-368">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="b0c61-369">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-369">Parameters</span></span>
* <span data-ttu-id="b0c61-370">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="b0c61-370">interface : network interface guid</span></span>
* <span data-ttu-id="b0c61-371">Профиль: имя профиля</span><span class="sxs-lookup"><span data-stu-id="b0c61-371">profile : profile name</span></span>

<span data-ttu-id="b0c61-372">**/АПИ/ВИФИ/Нетворкс (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-372">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="b0c61-373">Перечисляет беспроводные сети в указанном сетевом интерфейсе</span><span class="sxs-lookup"><span data-stu-id="b0c61-373">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="b0c61-374">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-374">Parameters</span></span>
* <span data-ttu-id="b0c61-375">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="b0c61-375">interface : network interface guid</span></span>

<span data-ttu-id="b0c61-376">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-376">Return data</span></span>
* <span data-ttu-id="b0c61-377">Список беспроводных сетей, обнаруженных в сетевом интерфейсе, с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="b0c61-377">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="b0c61-378">**/АПИ/ВИФИ/Нетворк (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-378">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="b0c61-379">Подключение к сети или отключение от него по указанному интерфейсу</span><span class="sxs-lookup"><span data-stu-id="b0c61-379">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="b0c61-380">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-380">Parameters</span></span>
* <span data-ttu-id="b0c61-381">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="b0c61-381">interface : network interface guid</span></span>
* <span data-ttu-id="b0c61-382">SSID: SSID, hex64 в кодировке для подключения</span><span class="sxs-lookup"><span data-stu-id="b0c61-382">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="b0c61-383">Операция: подключение или отключение</span><span class="sxs-lookup"><span data-stu-id="b0c61-383">op : connect or disconnect</span></span>
* <span data-ttu-id="b0c61-384">креатепрофиле: Да или нет</span><span class="sxs-lookup"><span data-stu-id="b0c61-384">createprofile : yes or no</span></span>
* <span data-ttu-id="b0c61-385">ключ: Shared Key, hex64 Encoded</span><span class="sxs-lookup"><span data-stu-id="b0c61-385">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="b0c61-386">Средство записи производительности Windows</span><span class="sxs-lookup"><span data-stu-id="b0c61-386">Windows Performance Recorder</span></span>

<span data-ttu-id="b0c61-387">**/АПИ/ВПР/кустомтраце (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-387">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="b0c61-388">Отправляет профиль ЗВЧ и начинает трассировку с помощью отправленного профиля.</span><span class="sxs-lookup"><span data-stu-id="b0c61-388">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="b0c61-389">Полезных данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-389">Payload</span></span>
* <span data-ttu-id="b0c61-390">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="b0c61-390">multi-part conforming http body</span></span>

<span data-ttu-id="b0c61-391">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-391">Return data</span></span>
* <span data-ttu-id="b0c61-392">Возвращает состояние сеанса WPR.</span><span class="sxs-lookup"><span data-stu-id="b0c61-392">Returns the WPR session status.</span></span>

<span data-ttu-id="b0c61-393">**/АПИ/ВПР/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-393">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="b0c61-394">Получение состояния сеанса ЗВЧ</span><span class="sxs-lookup"><span data-stu-id="b0c61-394">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="b0c61-395">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-395">Return data</span></span>
* <span data-ttu-id="b0c61-396">Состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="b0c61-396">WPR session status.</span></span>

<span data-ttu-id="b0c61-397">**/АПИ/ВПР/траце (GET)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-397">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="b0c61-398">Останавливает сеанс трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="b0c61-398">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="b0c61-399">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-399">Return data</span></span>
* <span data-ttu-id="b0c61-400">Возвращает ETL-файл трассировки</span><span class="sxs-lookup"><span data-stu-id="b0c61-400">Returns the trace ETL file</span></span>

<span data-ttu-id="b0c61-401">**/АПИ/ВПР/траце (POST)**</span><span class="sxs-lookup"><span data-stu-id="b0c61-401">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="b0c61-402">Запускает сеансы трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="b0c61-402">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="b0c61-403">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c61-403">Parameters</span></span>
* <span data-ttu-id="b0c61-404">профиля Имя профиля.</span><span class="sxs-lookup"><span data-stu-id="b0c61-404">profile : Profile name.</span></span> <span data-ttu-id="b0c61-405">Доступные профили хранятся в перфпрофилес/Profiles. JSON.</span><span class="sxs-lookup"><span data-stu-id="b0c61-405">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="b0c61-406">Возврат данных</span><span class="sxs-lookup"><span data-stu-id="b0c61-406">Return data</span></span>
* <span data-ttu-id="b0c61-407">При запуске возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="b0c61-407">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0c61-408">См. также</span><span class="sxs-lookup"><span data-stu-id="b0c61-408">See also</span></span>
* [<span data-ttu-id="b0c61-409">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="b0c61-409">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="b0c61-410">Справочник по API для базовых порталов устройств (UWP)</span><span class="sxs-lookup"><span data-stu-id="b0c61-410">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
