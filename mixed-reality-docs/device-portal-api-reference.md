---
title: Справочник по API портала устройств
description: Справочник по API для портала устройств Windows на HoloLens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, портал устройств Windows, API
ms.openlocfilehash: 17268c9a20d3da0ee90e5d6cead4342d3badf800
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451329"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="6f169-104">Справочник по API портала устройств</span><span class="sxs-lookup"><span data-stu-id="6f169-104">Device portal API reference</span></span>

<span data-ttu-id="6f169-105">Все на [портале устройств Windows](using-the-windows-device-portal.md) основаны на REST API, которые можно использовать для программного доступа к данным и управления устройством.</span><span class="sxs-lookup"><span data-stu-id="6f169-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="6f169-106">Развертывании приложения</span><span class="sxs-lookup"><span data-stu-id="6f169-106">App deloyment</span></span>

<span data-ttu-id="6f169-107">**/АПИ/АПП/паккажеманажер/паккаже (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6f169-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="6f169-108">Удаляет приложение.</span><span class="sxs-lookup"><span data-stu-id="6f169-108">Uninstalls an app</span></span>

<span data-ttu-id="6f169-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-109">Parameters</span></span>
* <span data-ttu-id="6f169-110">Пакет: имя файла удаляемого пакета.</span><span class="sxs-lookup"><span data-stu-id="6f169-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="6f169-111">**/АПИ/АПП/паккажеманажер/паккаже (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="6f169-112">Устанавливает приложение</span><span class="sxs-lookup"><span data-stu-id="6f169-112">Installs an App</span></span>

<span data-ttu-id="6f169-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-113">Parameters</span></span>
* <span data-ttu-id="6f169-114">Пакет: имя файла устанавливаемого пакета.</span><span class="sxs-lookup"><span data-stu-id="6f169-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="6f169-115">Payload</span><span class="sxs-lookup"><span data-stu-id="6f169-115">Payload</span></span>
* <span data-ttu-id="6f169-116">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="6f169-116">multi-part conforming http body</span></span>

<span data-ttu-id="6f169-117">**/АПИ/АПП/паккажеманажер/паккажес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="6f169-118">Извлекает список установленных приложений в системе со сведениями</span><span class="sxs-lookup"><span data-stu-id="6f169-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="6f169-119">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-119">Return data</span></span>
* <span data-ttu-id="6f169-120">Список установленных пакетов со сведениями</span><span class="sxs-lookup"><span data-stu-id="6f169-120">List of installed packages with details</span></span>

<span data-ttu-id="6f169-121">**/АПИ/АПП/паккажеманажер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="6f169-122">Возвращает состояние выполняющейся установки приложения.</span><span class="sxs-lookup"><span data-stu-id="6f169-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="6f169-123">Дамп коллекции</span><span class="sxs-lookup"><span data-stu-id="6f169-123">Dump collection</span></span>

<span data-ttu-id="6f169-124">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6f169-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="6f169-125">Отключает сбор аварийных дампов для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6f169-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="6f169-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-126">Parameters</span></span>
* <span data-ttu-id="6f169-127">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6f169-127">packageFullname : package name</span></span>

<span data-ttu-id="6f169-128">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="6f169-129">Получение параметров для коллекции аварийных дампов приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6f169-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="6f169-130">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-130">Parameters</span></span>
* <span data-ttu-id="6f169-131">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6f169-131">packageFullname : package name</span></span>

<span data-ttu-id="6f169-132">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="6f169-133">Включает и задает параметры управления дампом для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6f169-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="6f169-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-134">Parameters</span></span>
* <span data-ttu-id="6f169-135">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6f169-135">packageFullname : package name</span></span>

<span data-ttu-id="6f169-136">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6f169-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="6f169-137">Удаляет аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6f169-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="6f169-138">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-138">Parameters</span></span>
* <span data-ttu-id="6f169-139">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6f169-139">packageFullname : package name</span></span>
* <span data-ttu-id="6f169-140">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="6f169-140">fileName : dump file name</span></span>

<span data-ttu-id="6f169-141">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="6f169-142">Получает аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6f169-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="6f169-143">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-143">Parameters</span></span>
* <span data-ttu-id="6f169-144">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="6f169-144">packageFullname : package name</span></span>
* <span data-ttu-id="6f169-145">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="6f169-145">fileName : dump file name</span></span>

<span data-ttu-id="6f169-146">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-146">Return data</span></span>
* <span data-ttu-id="6f169-147">Файл дампа.</span><span class="sxs-lookup"><span data-stu-id="6f169-147">Dump file.</span></span> <span data-ttu-id="6f169-148">Проверка с помощью WinDbg или Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f169-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="6f169-149">**/АПИ/дебуг/ДУМП/усермоде/думпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="6f169-150">Возвращает список всех аварийных дампов для приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="6f169-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="6f169-151">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-151">Return data</span></span>
* <span data-ttu-id="6f169-152">Список аварийных дампов для приложения, загруженного на стороне</span><span class="sxs-lookup"><span data-stu-id="6f169-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="6f169-153">Трассировка событий Windows</span><span class="sxs-lookup"><span data-stu-id="6f169-153">ETW</span></span>

<span data-ttu-id="6f169-154">**/АПИ/ЕТВ/провидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="6f169-155">Перечисляет зарегистрированные поставщики</span><span class="sxs-lookup"><span data-stu-id="6f169-155">Enumerates registered providers</span></span>

<span data-ttu-id="6f169-156">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-156">Return data</span></span>
* <span data-ttu-id="6f169-157">Список поставщиков, понятное имя и идентификатор GUID</span><span class="sxs-lookup"><span data-stu-id="6f169-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="6f169-158">**/АПИ/ЕТВ/Сессион/реалтиме (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="6f169-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="6f169-159">Создает сеанс ETW в режиме реального времени; управляется через WebSocket.</span><span class="sxs-lookup"><span data-stu-id="6f169-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="6f169-160">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-160">Return data</span></span>
* <span data-ttu-id="6f169-161">События ETW из включенных поставщиков</span><span class="sxs-lookup"><span data-stu-id="6f169-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="6f169-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="6f169-162">Holographic OS</span></span>

<span data-ttu-id="6f169-163">**/АПИ/холографик/ОС/ЕТВ/кустомпровидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="6f169-164">Возвращает список поставщиков ETW, которые не зарегистрированы в системе.</span><span class="sxs-lookup"><span data-stu-id="6f169-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="6f169-165">**/АПИ/холографик/ОС/сервицес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="6f169-166">Возвращает состояния всех служб, на которых выполняются службы.</span><span class="sxs-lookup"><span data-stu-id="6f169-166">Returns the states of all services running.</span></span>

<span data-ttu-id="6f169-167">**/АПИ/холографик/ОС/Сеттингс/ИПД (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="6f169-168">Получает хранимую IPD (Интерпупиллари distance) в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="6f169-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="6f169-169">**/АПИ/холографик/ОС/Сеттингс/ИПД (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="6f169-170">Задает IPD</span><span class="sxs-lookup"><span data-stu-id="6f169-170">Sets the IPD</span></span>

<span data-ttu-id="6f169-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-171">Parameters</span></span>
* <span data-ttu-id="6f169-172">IPD: новое значение IPD для установки в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="6f169-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="6f169-173">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="6f169-174">Получение требований HTTPS для Портала устройств</span><span class="sxs-lookup"><span data-stu-id="6f169-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="6f169-175">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="6f169-176">Установка требований HTTPS для портала устройств</span><span class="sxs-lookup"><span data-stu-id="6f169-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="6f169-177">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-177">Parameters</span></span>
* <span data-ttu-id="6f169-178">обязательный: Да, нет или по умолчанию</span><span class="sxs-lookup"><span data-stu-id="6f169-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="6f169-179">Holographic восприятие</span><span class="sxs-lookup"><span data-stu-id="6f169-179">Holographic Perception</span></span>

<span data-ttu-id="6f169-180">**/АПИ/холографик/перцептион/клиент (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="6f169-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="6f169-181">Принимает обновления WebSocket и запускает клиент-восприятие, которое отправляет обновления с частотой 30 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="6f169-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="6f169-182">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-182">Parameters</span></span>
* <span data-ttu-id="6f169-183">клиентмоде: "Active" запускает режим отслеживания визуального элемента, если он не может быть установлен в пассивном режиме</span><span class="sxs-lookup"><span data-stu-id="6f169-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="6f169-184">Голограмма holographic</span><span class="sxs-lookup"><span data-stu-id="6f169-184">Holographic Thermal</span></span>

<span data-ttu-id="6f169-185">**/АПИ/холографик/сермал/стаже (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="6f169-186">Получите температурный этап устройства (0 нормальная, 1 тепло, 2 критическая)</span><span class="sxs-lookup"><span data-stu-id="6f169-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="6f169-187">Элемент управления имитацией восприятия</span><span class="sxs-lookup"><span data-stu-id="6f169-187">Perception Simulation Control</span></span>

<span data-ttu-id="6f169-188">**/АПИ/холографик/симулатион/контрол/моде (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="6f169-189">Получение режима моделирования</span><span class="sxs-lookup"><span data-stu-id="6f169-189">Get the simulation mode</span></span>

<span data-ttu-id="6f169-190">**/АПИ/холографик/симулатион/контрол/моде (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="6f169-191">Установка режима имитации</span><span class="sxs-lookup"><span data-stu-id="6f169-191">Set the simulation mode</span></span>

<span data-ttu-id="6f169-192">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-192">Parameters</span></span>
* <span data-ttu-id="6f169-193">режим: режим имитации: по умолчанию, имитация, удаленный, устаревший</span><span class="sxs-lookup"><span data-stu-id="6f169-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="6f169-194">**/АПИ/холографик/симулатион/контрол/стреам (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6f169-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="6f169-195">Удаляет поток управления.</span><span class="sxs-lookup"><span data-stu-id="6f169-195">Delete a control stream.</span></span>

<span data-ttu-id="6f169-196">**/АПИ/холографик/симулатион/контрол/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="6f169-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="6f169-197">Откройте подключение к веб-сокету для потока управления.</span><span class="sxs-lookup"><span data-stu-id="6f169-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="6f169-198">**/АПИ/холографик/симулатион/контрол/стреам (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="6f169-199">Создайте поток управления (требуется приоритет) или опубликуйте данные в созданном потоке (требуется streamId).</span><span class="sxs-lookup"><span data-stu-id="6f169-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="6f169-200">Ожидаемые данные должны иметь тип "Application/октет-Stream".</span><span class="sxs-lookup"><span data-stu-id="6f169-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="6f169-201">**/АПИ/холографик/симулатион/дисплай/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="6f169-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="6f169-202">Запросите поток видео имитации, содержащий содержимое, отображаемое для отображения в системе, в режиме "имитация".</span><span class="sxs-lookup"><span data-stu-id="6f169-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="6f169-203">Сначала будет отправлен заголовок простого дескриптора формата, а затем H. 264-Encoded текстуры, в каждой из которых предшествует заголовок, указывающий индекс глаза и размер текстуры.</span><span class="sxs-lookup"><span data-stu-id="6f169-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="6f169-204">Воспроизведение имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="6f169-204">Perception Simulation Playback</span></span>

<span data-ttu-id="6f169-205">**/АПИ/холографик/симулатион/плайбакк/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6f169-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="6f169-206">Удаление записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-206">Delete a recording.</span></span>

<span data-ttu-id="6f169-207">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-207">Parameters</span></span>
* <span data-ttu-id="6f169-208">запись: имя записи для удаления.</span><span class="sxs-lookup"><span data-stu-id="6f169-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="6f169-209">**/АПИ/холографик/симулатион/плайбакк/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="6f169-210">Отправьте запись.</span><span class="sxs-lookup"><span data-stu-id="6f169-210">Upload a recording.</span></span>

<span data-ttu-id="6f169-211">**/АПИ/холографик/симулатион/плайбакк/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="6f169-212">Получение всех записей.</span><span class="sxs-lookup"><span data-stu-id="6f169-212">Get all recordings.</span></span>

<span data-ttu-id="6f169-213">**/АПИ/холографик/симулатион/плайбакк/Сессион (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="6f169-214">Получение текущего состояния воспроизведения записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="6f169-215">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-215">Parameters</span></span>
* <span data-ttu-id="6f169-216">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-216">recording : Name of recording.</span></span>

<span data-ttu-id="6f169-217">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6f169-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="6f169-218">Выгрузить запись.</span><span class="sxs-lookup"><span data-stu-id="6f169-218">Unload a recording.</span></span>

<span data-ttu-id="6f169-219">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-219">Parameters</span></span>
* <span data-ttu-id="6f169-220">запись: имя записи для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="6f169-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="6f169-221">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="6f169-222">Загрузка записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-222">Load a recording.</span></span>

<span data-ttu-id="6f169-223">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-223">Parameters</span></span>
* <span data-ttu-id="6f169-224">запись: имя загружаемой записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="6f169-225">**/АПИ/холографик/симулатион/плайбакк/Сессион/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="6f169-226">Получение всех загруженных записей.</span><span class="sxs-lookup"><span data-stu-id="6f169-226">Get all loaded recordings.</span></span>

<span data-ttu-id="6f169-227">**/АПИ/холографик/симулатион/плайбакк/Сессион/паусе (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="6f169-228">Приостановка записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-228">Pause a recording.</span></span>

<span data-ttu-id="6f169-229">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-229">Parameters</span></span>
* <span data-ttu-id="6f169-230">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-230">recording : Name of recording.</span></span>

<span data-ttu-id="6f169-231">**/АПИ/холографик/симулатион/плайбакк/Сессион/Плай (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="6f169-232">Воспроизведение записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-232">Play a recording.</span></span>

<span data-ttu-id="6f169-233">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-233">Parameters</span></span>
* <span data-ttu-id="6f169-234">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-234">recording : Name of recording.</span></span>

<span data-ttu-id="6f169-235">**/АПИ/холографик/симулатион/плайбакк/Сессион/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="6f169-236">Останавливает запись.</span><span class="sxs-lookup"><span data-stu-id="6f169-236">Stop a recording.</span></span>

<span data-ttu-id="6f169-237">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-237">Parameters</span></span>
* <span data-ttu-id="6f169-238">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-238">recording : Name of recording.</span></span>

<span data-ttu-id="6f169-239">**/АПИ/холографик/симулатион/плайбакк/Сессион/типес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="6f169-240">Получение типов данных в загруженной записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="6f169-241">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-241">Parameters</span></span>
* <span data-ttu-id="6f169-242">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="6f169-243">Запись имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="6f169-243">Perception Simulation Recording</span></span>

<span data-ttu-id="6f169-244">**/АПИ/холографик/симулатион/рекординг/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="6f169-245">Начать запись.</span><span class="sxs-lookup"><span data-stu-id="6f169-245">Start a recording.</span></span> <span data-ttu-id="6f169-246">Одновременно может быть активна только одна запись.</span><span class="sxs-lookup"><span data-stu-id="6f169-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="6f169-247">Необходимо задать один из головок, «руки», «Спатиалмаппинг» или «среда».</span><span class="sxs-lookup"><span data-stu-id="6f169-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="6f169-248">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-248">Parameters</span></span>
* <span data-ttu-id="6f169-249">Head: задайте значение 1, чтобы записать данные заголовка.</span><span class="sxs-lookup"><span data-stu-id="6f169-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="6f169-250">стрелки: значение 1, чтобы записать данные.</span><span class="sxs-lookup"><span data-stu-id="6f169-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="6f169-251">Спатиалмаппинг: задайте значение 1 для записи пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="6f169-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="6f169-252">окружение: задайте значение 1, чтобы записать данные среды.</span><span class="sxs-lookup"><span data-stu-id="6f169-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="6f169-253">имя. имя записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-253">name : Name of the recording.</span></span>
* <span data-ttu-id="6f169-254">Синглеспатиалмаппингфраме: задайте значение 1, чтобы записать только один фрейм пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="6f169-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="6f169-255">**/АПИ/холографик/симулатион/рекординг/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="6f169-256">Получение состояния записи.</span><span class="sxs-lookup"><span data-stu-id="6f169-256">Get recording state.</span></span>

<span data-ttu-id="6f169-257">**/АПИ/холографик/симулатион/рекординг/стоп (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="6f169-258">Останавливает текущую запись.</span><span class="sxs-lookup"><span data-stu-id="6f169-258">Stop the current recording.</span></span> <span data-ttu-id="6f169-259">Запись будет возвращена в виде файла.</span><span class="sxs-lookup"><span data-stu-id="6f169-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="6f169-260">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="6f169-260">Mixed Reality Capture</span></span>

<span data-ttu-id="6f169-261">**/АПИ/холографик/МРК/филе (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="6f169-262">Скачивает файл смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="6f169-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="6f169-263">Use Op = потоковый параметр запроса для потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="6f169-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="6f169-264">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-264">Parameters</span></span>
* <span data-ttu-id="6f169-265">имя файла: имя, hex64 в кодировке для получаемого видео.</span><span class="sxs-lookup"><span data-stu-id="6f169-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="6f169-266">Op: Stream</span><span class="sxs-lookup"><span data-stu-id="6f169-266">op : stream</span></span>

<span data-ttu-id="6f169-267">**/АПИ/холографик/МРК/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6f169-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="6f169-268">Удаляет запись смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="6f169-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="6f169-269">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-269">Parameters</span></span>
* <span data-ttu-id="6f169-270">filename: Name, hex64 Encoded (имя файла), которое нужно удалить.</span><span class="sxs-lookup"><span data-stu-id="6f169-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="6f169-271">**/АПИ/холографик/МРК/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="6f169-272">Возвращает список файлов смешанной реальности, хранящихся на устройстве</span><span class="sxs-lookup"><span data-stu-id="6f169-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="6f169-273">**/АПИ/холографик/МРК/фото (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="6f169-274">Принимает фотографию смешанной реальности и создает файл на устройстве</span><span class="sxs-lookup"><span data-stu-id="6f169-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="6f169-275">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-275">Parameters</span></span>
* <span data-ttu-id="6f169-276">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6f169-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="6f169-277">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6f169-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="6f169-278">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="6f169-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="6f169-279">**/АПИ/холографик/МРК/Сеттингс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="6f169-280">Получает параметры записи смешанной реальности по умолчанию</span><span class="sxs-lookup"><span data-stu-id="6f169-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="6f169-281">**/АПИ/холографик/МРК/Сеттингс (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="6f169-282">Задает параметры записи смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6f169-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="6f169-283">Некоторые из этих параметров применяются к фотографии и видеозаписи системы требований к системе.</span><span class="sxs-lookup"><span data-stu-id="6f169-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="6f169-284">**/АПИ/холографик/МРК/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="6f169-285">Возвращает состояние захвата смешанной реальности на портале устройств Windows.</span><span class="sxs-lookup"><span data-stu-id="6f169-285">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="6f169-286">***Ответ***</span><span class="sxs-lookup"><span data-stu-id="6f169-286">***Response***</span></span>

<span data-ttu-id="6f169-287">Ответ содержит свойство JSON, указывающее, записывается ли видео на портале устройств Windows.</span><span class="sxs-lookup"><span data-stu-id="6f169-287">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="6f169-288">**/АПИ/холографик/МРК/сумбнаил (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-288">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="6f169-289">Получает эскиз изображения для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="6f169-289">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="6f169-290">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-290">Parameters</span></span>
* <span data-ttu-id="6f169-291">filename: Name, hex64 Encoded, файла, для которого запрашивается эскиз.</span><span class="sxs-lookup"><span data-stu-id="6f169-291">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="6f169-292">**/АПИ/холографик/МРК/видео/контрол/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-292">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="6f169-293">Запуск записи смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="6f169-293">Starts a mixed reality recording</span></span>

<span data-ttu-id="6f169-294">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-294">Parameters</span></span>
* <span data-ttu-id="6f169-295">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6f169-295">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="6f169-296">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6f169-296">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="6f169-297">MIC: записать микрофон: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6f169-297">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="6f169-298">замыкание на себя: запись звука приложения: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6f169-298">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="6f169-299">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="6f169-299">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="6f169-300">встаб: (только HoloLens 2) Enable Video стабилизации: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="6f169-300">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="6f169-301">встаббуффер: (только HoloLens 2) задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="6f169-301">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="6f169-302">**/АПИ/холографик/МРК/видео/контрол/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-302">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="6f169-303">Останавливает текущую запись смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="6f169-303">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="6f169-304">Потоковая передача смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="6f169-304">Mixed Reality Streaming</span></span>

<span data-ttu-id="6f169-305">HoloLens поддерживает динамическую предварительную версию смешанной реальности через частную загрузку фрагментированного MP4.</span><span class="sxs-lookup"><span data-stu-id="6f169-305">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="6f169-306">Потоки смешанной реальности используют один и тот же набор параметров для управления тем, что захватывается:</span><span class="sxs-lookup"><span data-stu-id="6f169-306">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="6f169-307">Холо: голограммы записи: true или false</span><span class="sxs-lookup"><span data-stu-id="6f169-307">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="6f169-308">ПС: запись камеры PV: true или false</span><span class="sxs-lookup"><span data-stu-id="6f169-308">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="6f169-309">микрофон: записать микрофон: true или false</span><span class="sxs-lookup"><span data-stu-id="6f169-309">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="6f169-310">замыкание на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="6f169-310">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="6f169-311">Если ни один из этих элементов не указан: будут записываться голограммы, Фото-и видеокамера и звук приложения</span><span class="sxs-lookup"><span data-stu-id="6f169-311">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="6f169-312">Если таковые имеются, то по умолчанию для неуказанных параметров будет задано значение false.</span><span class="sxs-lookup"><span data-stu-id="6f169-312">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="6f169-313">Необязательные параметры (только HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="6f169-313">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="6f169-314">Рендерфромкамера: прорисовка с точки зрения фотографии или видеокамеры: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="6f169-314">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="6f169-315">встаб: enable Video стабилизации: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="6f169-315">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="6f169-316">встаббуффер: задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="6f169-316">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="6f169-317">**/API/holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-317">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="6f169-318">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="6f169-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="6f169-319">**/АПИ/холографик/стреам/live_high. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-319">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="6f169-320">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="6f169-320">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="6f169-321">**/АПИ/холографик/стреам/live_med. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-321">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="6f169-322">Поток 854x480p 30fps 2.5 Мбит.</span><span class="sxs-lookup"><span data-stu-id="6f169-322">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="6f169-323">**/АПИ/холографик/стреам/live_low. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-323">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="6f169-324">Поток 428x240p 15fps 0,6 Мбит.</span><span class="sxs-lookup"><span data-stu-id="6f169-324">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="6f169-325">Сеть</span><span class="sxs-lookup"><span data-stu-id="6f169-325">Networking</span></span>

<span data-ttu-id="6f169-326">**/АПИ/нетворкинг/ипконфиг (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-326">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="6f169-327">Возвращает текущую IP-конфигурацию</span><span class="sxs-lookup"><span data-stu-id="6f169-327">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="6f169-328">Сведения о ОС</span><span class="sxs-lookup"><span data-stu-id="6f169-328">OS Information</span></span>

<span data-ttu-id="6f169-329">**/АПИ/ОС/Инфо (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-329">**/api/os/info (GET)**</span></span>

<span data-ttu-id="6f169-330">Получение сведений об операционной системе</span><span class="sxs-lookup"><span data-stu-id="6f169-330">Gets operating system information</span></span>

<span data-ttu-id="6f169-331">**/АПИ/ОС/мачиненаме (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-331">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="6f169-332">Возвращает имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="6f169-332">Gets the machine name</span></span>

<span data-ttu-id="6f169-333">**/АПИ/ОС/мачиненаме (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-333">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="6f169-334">Задает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="6f169-334">Sets the machine name</span></span>

<span data-ttu-id="6f169-335">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-335">Parameters</span></span>
* <span data-ttu-id="6f169-336">Имя: новое имя компьютера, hex64 в кодировке, для которого задано значение.</span><span class="sxs-lookup"><span data-stu-id="6f169-336">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="6f169-337">Данные о производительности</span><span class="sxs-lookup"><span data-stu-id="6f169-337">Performance data</span></span>

<span data-ttu-id="6f169-338">**/АПИ/ресаурцеманажер/процессес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-338">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="6f169-339">Возвращает список запущенных процессов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="6f169-339">Returns the list of running processes with details</span></span>

<span data-ttu-id="6f169-340">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-340">Return data</span></span>
* <span data-ttu-id="6f169-341">JSON со списком процессов и сведений для каждого процесса</span><span class="sxs-lookup"><span data-stu-id="6f169-341">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="6f169-342">**/АПИ/ресаурцеманажер/системперф (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-342">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="6f169-343">Возвращает статистику производительности системы (операции чтения и записи ввода-вывода, статистика памяти и т. д.).</span><span class="sxs-lookup"><span data-stu-id="6f169-343">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="6f169-344">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-344">Return data</span></span>
* <span data-ttu-id="6f169-345">JSON со сведениями о системе: ЦП, GPU, память, сеть, IO</span><span class="sxs-lookup"><span data-stu-id="6f169-345">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="6f169-346">Мощный</span><span class="sxs-lookup"><span data-stu-id="6f169-346">Power</span></span>

<span data-ttu-id="6f169-347">**/АПИ/повер/Баттери (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-347">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="6f169-348">Возвращает текущее состояние аккумулятора</span><span class="sxs-lookup"><span data-stu-id="6f169-348">Gets the current battery state</span></span>

<span data-ttu-id="6f169-349">**/АПИ/повер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-349">**/api/power/state (GET)**</span></span>

<span data-ttu-id="6f169-350">Проверяет, находится ли система в состоянии с низким энергопотреблением</span><span class="sxs-lookup"><span data-stu-id="6f169-350">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="6f169-351">Удаленное управление</span><span class="sxs-lookup"><span data-stu-id="6f169-351">Remote Control</span></span>

<span data-ttu-id="6f169-352">**/АПИ/контрол/рестарт (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-352">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="6f169-353">Перезапускает целевое устройство</span><span class="sxs-lookup"><span data-stu-id="6f169-353">Restarts the target device</span></span>

<span data-ttu-id="6f169-354">**/АПИ/контрол/шутдовн (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-354">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="6f169-355">Завершает работу целевого устройства</span><span class="sxs-lookup"><span data-stu-id="6f169-355">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="6f169-356">Диспетчер задач</span><span class="sxs-lookup"><span data-stu-id="6f169-356">Task Manager</span></span>

<span data-ttu-id="6f169-357">**/АПИ/таскманажер/АПП (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6f169-357">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="6f169-358">Останавливает современное приложение</span><span class="sxs-lookup"><span data-stu-id="6f169-358">Stops a modern app</span></span>

<span data-ttu-id="6f169-359">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-359">Parameters</span></span>
* <span data-ttu-id="6f169-360">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="6f169-360">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="6f169-361">форцестоп: принудительно останавливаются все процессы (= да)</span><span class="sxs-lookup"><span data-stu-id="6f169-361">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="6f169-362">**/АПИ/таскманажер/АПП (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-362">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="6f169-363">Запуск современного приложения</span><span class="sxs-lookup"><span data-stu-id="6f169-363">Starts a modern app</span></span>

<span data-ttu-id="6f169-364">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-364">Parameters</span></span>
* <span data-ttu-id="6f169-365">AppID: ПРАИД приложения для запуска, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="6f169-365">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="6f169-366">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="6f169-366">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="6f169-367">Управление Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="6f169-367">WiFi Management</span></span>

<span data-ttu-id="6f169-368">**/АПИ/ВИФИ/интерфацес (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-368">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="6f169-369">Перечисляет беспроводные сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="6f169-369">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="6f169-370">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-370">Return data</span></span>
* <span data-ttu-id="6f169-371">Список беспроводных интерфейсов с подробными сведениями (GUID, описание и т. д.).</span><span class="sxs-lookup"><span data-stu-id="6f169-371">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="6f169-372">**/АПИ/ВИФИ/Нетворк (удаление)**</span><span class="sxs-lookup"><span data-stu-id="6f169-372">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="6f169-373">Удаление профиля, связанного с сетью, в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="6f169-373">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="6f169-374">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-374">Parameters</span></span>
* <span data-ttu-id="6f169-375">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="6f169-375">interface : network interface guid</span></span>
* <span data-ttu-id="6f169-376">Профиль: имя профиля</span><span class="sxs-lookup"><span data-stu-id="6f169-376">profile : profile name</span></span>

<span data-ttu-id="6f169-377">**/АПИ/ВИФИ/Нетворкс (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-377">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="6f169-378">Перечисляет беспроводные сети в указанном сетевом интерфейсе</span><span class="sxs-lookup"><span data-stu-id="6f169-378">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="6f169-379">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-379">Parameters</span></span>
* <span data-ttu-id="6f169-380">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="6f169-380">interface : network interface guid</span></span>

<span data-ttu-id="6f169-381">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-381">Return data</span></span>
* <span data-ttu-id="6f169-382">Список беспроводных сетей, обнаруженных в сетевом интерфейсе, с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="6f169-382">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="6f169-383">**/АПИ/ВИФИ/Нетворк (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-383">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="6f169-384">Подключение к сети или отключение от него по указанному интерфейсу</span><span class="sxs-lookup"><span data-stu-id="6f169-384">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="6f169-385">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-385">Parameters</span></span>
* <span data-ttu-id="6f169-386">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="6f169-386">interface : network interface guid</span></span>
* <span data-ttu-id="6f169-387">SSID: SSID, hex64 в кодировке для подключения</span><span class="sxs-lookup"><span data-stu-id="6f169-387">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="6f169-388">Операция: подключение или отключение</span><span class="sxs-lookup"><span data-stu-id="6f169-388">op : connect or disconnect</span></span>
* <span data-ttu-id="6f169-389">креатепрофиле: Да или нет</span><span class="sxs-lookup"><span data-stu-id="6f169-389">createprofile : yes or no</span></span>
* <span data-ttu-id="6f169-390">ключ: Shared Key, hex64 Encoded</span><span class="sxs-lookup"><span data-stu-id="6f169-390">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="6f169-391">Средство записи производительности Windows</span><span class="sxs-lookup"><span data-stu-id="6f169-391">Windows Performance Recorder</span></span>

<span data-ttu-id="6f169-392">**/АПИ/ВПР/кустомтраце (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-392">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="6f169-393">Отправляет профиль ЗВЧ и начинает трассировку с помощью отправленного профиля.</span><span class="sxs-lookup"><span data-stu-id="6f169-393">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="6f169-394">Payload</span><span class="sxs-lookup"><span data-stu-id="6f169-394">Payload</span></span>
* <span data-ttu-id="6f169-395">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="6f169-395">multi-part conforming http body</span></span>

<span data-ttu-id="6f169-396">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-396">Return data</span></span>
* <span data-ttu-id="6f169-397">Возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="6f169-397">Returns the WPR session status.</span></span>

<span data-ttu-id="6f169-398">**/АПИ/ВПР/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-398">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="6f169-399">Получение состояния сеанса ЗВЧ</span><span class="sxs-lookup"><span data-stu-id="6f169-399">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="6f169-400">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-400">Return data</span></span>
* <span data-ttu-id="6f169-401">Состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="6f169-401">WPR session status.</span></span>

<span data-ttu-id="6f169-402">**/АПИ/ВПР/траце (GET)**</span><span class="sxs-lookup"><span data-stu-id="6f169-402">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="6f169-403">Останавливает сеанс трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="6f169-403">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="6f169-404">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-404">Return data</span></span>
* <span data-ttu-id="6f169-405">Возвращает ETL-файл трассировки</span><span class="sxs-lookup"><span data-stu-id="6f169-405">Returns the trace ETL file</span></span>

<span data-ttu-id="6f169-406">**/АПИ/ВПР/траце (POST)**</span><span class="sxs-lookup"><span data-stu-id="6f169-406">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="6f169-407">Запускает сеансы трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="6f169-407">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="6f169-408">Параметры</span><span class="sxs-lookup"><span data-stu-id="6f169-408">Parameters</span></span>
* <span data-ttu-id="6f169-409">Профиль: имя профиля.</span><span class="sxs-lookup"><span data-stu-id="6f169-409">profile : Profile name.</span></span> <span data-ttu-id="6f169-410">Доступные профили хранятся в перфпрофилес/Profiles. JSON.</span><span class="sxs-lookup"><span data-stu-id="6f169-410">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="6f169-411">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="6f169-411">Return data</span></span>
* <span data-ttu-id="6f169-412">При запуске возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="6f169-412">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f169-413">См. также</span><span class="sxs-lookup"><span data-stu-id="6f169-413">See also</span></span>
* [<span data-ttu-id="6f169-414">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="6f169-414">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="6f169-415">Справочник по API для базовых порталов устройств (UWP)</span><span class="sxs-lookup"><span data-stu-id="6f169-415">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
