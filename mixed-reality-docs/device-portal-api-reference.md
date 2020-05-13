---
title: Справочник по API портала устройств
description: Справочник по API для портала устройств Windows на HoloLens
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, портал устройств Windows, API
ms.openlocfilehash: 8c9d60f458cddd3ba258aed0ee82f7aa16c10ba6
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83227968"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="84464-104">Справочник по API портала устройств</span><span class="sxs-lookup"><span data-stu-id="84464-104">Device portal API reference</span></span>

<span data-ttu-id="84464-105">Все на [портале устройств Windows](using-the-windows-device-portal.md) основаны на REST API, которые можно использовать для программного доступа к данным и управления устройством.</span><span class="sxs-lookup"><span data-stu-id="84464-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="84464-106">Развертывании приложения</span><span class="sxs-lookup"><span data-stu-id="84464-106">App deloyment</span></span>

<span data-ttu-id="84464-107">**/АПИ/АПП/паккажеманажер/паккаже (удаление)**</span><span class="sxs-lookup"><span data-stu-id="84464-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="84464-108">Удаляет приложение.</span><span class="sxs-lookup"><span data-stu-id="84464-108">Uninstalls an app</span></span>

<span data-ttu-id="84464-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-109">Parameters</span></span>
* <span data-ttu-id="84464-110">Пакет: имя файла удаляемого пакета.</span><span class="sxs-lookup"><span data-stu-id="84464-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="84464-111">**/АПИ/АПП/паккажеманажер/паккаже (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="84464-112">Устанавливает приложение</span><span class="sxs-lookup"><span data-stu-id="84464-112">Installs an App</span></span>

<span data-ttu-id="84464-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-113">Parameters</span></span>
* <span data-ttu-id="84464-114">Пакет: имя файла устанавливаемого пакета.</span><span class="sxs-lookup"><span data-stu-id="84464-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="84464-115">Полезные данные</span><span class="sxs-lookup"><span data-stu-id="84464-115">Payload</span></span>
* <span data-ttu-id="84464-116">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="84464-116">multi-part conforming http body</span></span>

<span data-ttu-id="84464-117">**/АПИ/АПП/паккажеманажер/паккажес (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="84464-118">Извлекает список установленных приложений в системе со сведениями</span><span class="sxs-lookup"><span data-stu-id="84464-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="84464-119">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-119">Return data</span></span>
* <span data-ttu-id="84464-120">Список установленных пакетов со сведениями</span><span class="sxs-lookup"><span data-stu-id="84464-120">List of installed packages with details</span></span>

<span data-ttu-id="84464-121">**/АПИ/АПП/паккажеманажер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="84464-122">Возвращает состояние выполняющейся установки приложения.</span><span class="sxs-lookup"><span data-stu-id="84464-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="84464-123">Дамп коллекции</span><span class="sxs-lookup"><span data-stu-id="84464-123">Dump collection</span></span>

<span data-ttu-id="84464-124">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (удаление)**</span><span class="sxs-lookup"><span data-stu-id="84464-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="84464-125">Отключает сбор аварийных дампов для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="84464-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="84464-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-126">Parameters</span></span>
* <span data-ttu-id="84464-127">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="84464-127">packageFullname : package name</span></span>

<span data-ttu-id="84464-128">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="84464-129">Получение параметров для коллекции аварийных дампов приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="84464-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="84464-130">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-130">Parameters</span></span>
* <span data-ttu-id="84464-131">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="84464-131">packageFullname : package name</span></span>

<span data-ttu-id="84464-132">**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="84464-133">Включает и задает параметры управления дампом для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="84464-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="84464-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-134">Parameters</span></span>
* <span data-ttu-id="84464-135">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="84464-135">packageFullname : package name</span></span>

<span data-ttu-id="84464-136">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (удаление)**</span><span class="sxs-lookup"><span data-stu-id="84464-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="84464-137">Удаляет аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="84464-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="84464-138">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-138">Parameters</span></span>
* <span data-ttu-id="84464-139">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="84464-139">packageFullname : package name</span></span>
* <span data-ttu-id="84464-140">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="84464-140">fileName : dump file name</span></span>

<span data-ttu-id="84464-141">**/АПИ/дебуг/ДУМП/усермоде/крашдумп (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="84464-142">Получает аварийный дамп для приложения загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="84464-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="84464-143">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-143">Parameters</span></span>
* <span data-ttu-id="84464-144">Полноеимяпакета: имя пакета</span><span class="sxs-lookup"><span data-stu-id="84464-144">packageFullname : package name</span></span>
* <span data-ttu-id="84464-145">имя_файла: имя файла дампа</span><span class="sxs-lookup"><span data-stu-id="84464-145">fileName : dump file name</span></span>

<span data-ttu-id="84464-146">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-146">Return data</span></span>
* <span data-ttu-id="84464-147">Файл дампа.</span><span class="sxs-lookup"><span data-stu-id="84464-147">Dump file.</span></span> <span data-ttu-id="84464-148">Проверка с помощью WinDbg или Visual Studio</span><span class="sxs-lookup"><span data-stu-id="84464-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="84464-149">**/АПИ/дебуг/ДУМП/усермоде/думпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="84464-150">Возвращает список всех аварийных дампов для приложений загруженные неопубликованные</span><span class="sxs-lookup"><span data-stu-id="84464-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="84464-151">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-151">Return data</span></span>
* <span data-ttu-id="84464-152">Список аварийных дампов для приложения, загруженного на стороне</span><span class="sxs-lookup"><span data-stu-id="84464-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="84464-153">Трассировка событий Windows</span><span class="sxs-lookup"><span data-stu-id="84464-153">ETW</span></span>

<span data-ttu-id="84464-154">**/АПИ/ЕТВ/провидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="84464-155">Перечисляет зарегистрированные поставщики</span><span class="sxs-lookup"><span data-stu-id="84464-155">Enumerates registered providers</span></span>

<span data-ttu-id="84464-156">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-156">Return data</span></span>
* <span data-ttu-id="84464-157">Список поставщиков, понятное имя и идентификатор GUID</span><span class="sxs-lookup"><span data-stu-id="84464-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="84464-158">**/АПИ/ЕТВ/Сессион/реалтиме (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="84464-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="84464-159">Создает сеанс ETW в режиме реального времени; управляется через WebSocket.</span><span class="sxs-lookup"><span data-stu-id="84464-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="84464-160">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-160">Return data</span></span>
* <span data-ttu-id="84464-161">События ETW из включенных поставщиков</span><span class="sxs-lookup"><span data-stu-id="84464-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="84464-162">Holographic OS</span><span class="sxs-lookup"><span data-stu-id="84464-162">Holographic OS</span></span>

<span data-ttu-id="84464-163">**/АПИ/холографик/ОС/ЕТВ/кустомпровидерс (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="84464-164">Возвращает список поставщиков ETW, которые не зарегистрированы в системе.</span><span class="sxs-lookup"><span data-stu-id="84464-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="84464-165">**/АПИ/холографик/ОС/сервицес (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="84464-166">Возвращает состояния всех служб, на которых выполняются службы.</span><span class="sxs-lookup"><span data-stu-id="84464-166">Returns the states of all services running.</span></span>

<span data-ttu-id="84464-167">**/АПИ/холографик/ОС/Сеттингс/ИПД (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="84464-168">Получает хранимую IPD (Интерпупиллари distance) в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="84464-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="84464-169">**/АПИ/холографик/ОС/Сеттингс/ИПД (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="84464-170">Задает IPD</span><span class="sxs-lookup"><span data-stu-id="84464-170">Sets the IPD</span></span>

<span data-ttu-id="84464-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-171">Parameters</span></span>
* <span data-ttu-id="84464-172">IPD: новое значение IPD для установки в миллиметрах</span><span class="sxs-lookup"><span data-stu-id="84464-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="84464-173">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="84464-174">Получение требований HTTPS для Портала устройств</span><span class="sxs-lookup"><span data-stu-id="84464-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="84464-175">**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="84464-176">Установка требований HTTPS для портала устройств</span><span class="sxs-lookup"><span data-stu-id="84464-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="84464-177">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-177">Parameters</span></span>
* <span data-ttu-id="84464-178">обязательный: Да, нет или по умолчанию</span><span class="sxs-lookup"><span data-stu-id="84464-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="84464-179">Holographic восприятие</span><span class="sxs-lookup"><span data-stu-id="84464-179">Holographic Perception</span></span>

<span data-ttu-id="84464-180">**/АПИ/холографик/перцептион/клиент (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="84464-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="84464-181">Принимает обновления WebSocket и запускает клиент-восприятие, которое отправляет обновления с частотой 30 кадров/с.</span><span class="sxs-lookup"><span data-stu-id="84464-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="84464-182">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-182">Parameters</span></span>
* <span data-ttu-id="84464-183">клиентмоде: "Active" запускает режим отслеживания визуального элемента, если он не может быть установлен в пассивном режиме</span><span class="sxs-lookup"><span data-stu-id="84464-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="84464-184">Голограмма holographic</span><span class="sxs-lookup"><span data-stu-id="84464-184">Holographic Thermal</span></span>

<span data-ttu-id="84464-185">**/АПИ/холографик/сермал/стаже (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="84464-186">Получите температурный этап устройства (0 нормальная, 1 тепло, 2 критическая)</span><span class="sxs-lookup"><span data-stu-id="84464-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="84464-187">Элемент управления имитацией восприятия</span><span class="sxs-lookup"><span data-stu-id="84464-187">Perception Simulation Control</span></span>

<span data-ttu-id="84464-188">**/АПИ/холографик/симулатион/контрол/моде (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-188">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="84464-189">Получение режима моделирования</span><span class="sxs-lookup"><span data-stu-id="84464-189">Get the simulation mode</span></span>

<span data-ttu-id="84464-190">**/АПИ/холографик/симулатион/контрол/моде (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-190">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="84464-191">Установка режима имитации</span><span class="sxs-lookup"><span data-stu-id="84464-191">Set the simulation mode</span></span>

<span data-ttu-id="84464-192">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-192">Parameters</span></span>
* <span data-ttu-id="84464-193">режим: режим имитации: по умолчанию, имитация, удаленный, устаревший</span><span class="sxs-lookup"><span data-stu-id="84464-193">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="84464-194">**/АПИ/холографик/симулатион/контрол/стреам (удаление)**</span><span class="sxs-lookup"><span data-stu-id="84464-194">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="84464-195">Удаляет поток управления.</span><span class="sxs-lookup"><span data-stu-id="84464-195">Delete a control stream.</span></span>

<span data-ttu-id="84464-196">**/АПИ/холографик/симулатион/контрол/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="84464-196">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="84464-197">Откройте подключение к веб-сокету для потока управления.</span><span class="sxs-lookup"><span data-stu-id="84464-197">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="84464-198">**/АПИ/холографик/симулатион/контрол/стреам (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-198">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="84464-199">Создайте поток управления (требуется приоритет) или опубликуйте данные в созданном потоке (требуется streamId).</span><span class="sxs-lookup"><span data-stu-id="84464-199">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="84464-200">Ожидаемые данные должны иметь тип "Application/октет-Stream".</span><span class="sxs-lookup"><span data-stu-id="84464-200">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="84464-201">**/АПИ/холографик/симулатион/дисплай/стреам (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="84464-201">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="84464-202">Запросите поток видео имитации, содержащий содержимое, отображаемое для отображения в системе, в режиме "имитация".</span><span class="sxs-lookup"><span data-stu-id="84464-202">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="84464-203">Сначала будет отправлен заголовок простого дескриптора формата, а затем H. 264-Encoded текстуры, в каждой из которых предшествует заголовок, указывающий индекс глаза и размер текстуры.</span><span class="sxs-lookup"><span data-stu-id="84464-203">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="84464-204">Воспроизведение имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="84464-204">Perception Simulation Playback</span></span>

<span data-ttu-id="84464-205">**/АПИ/холографик/симулатион/плайбакк/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="84464-205">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="84464-206">Удаление записи.</span><span class="sxs-lookup"><span data-stu-id="84464-206">Delete a recording.</span></span>

<span data-ttu-id="84464-207">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-207">Parameters</span></span>
* <span data-ttu-id="84464-208">запись: имя записи для удаления.</span><span class="sxs-lookup"><span data-stu-id="84464-208">recording : Name of recording to delete.</span></span>

<span data-ttu-id="84464-209">**/АПИ/холографик/симулатион/плайбакк/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-209">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="84464-210">Отправьте запись.</span><span class="sxs-lookup"><span data-stu-id="84464-210">Upload a recording.</span></span>

<span data-ttu-id="84464-211">**/АПИ/холографик/симулатион/плайбакк/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-211">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="84464-212">Получение всех записей.</span><span class="sxs-lookup"><span data-stu-id="84464-212">Get all recordings.</span></span>

<span data-ttu-id="84464-213">**/АПИ/холографик/симулатион/плайбакк/Сессион (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-213">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="84464-214">Получение текущего состояния воспроизведения записи.</span><span class="sxs-lookup"><span data-stu-id="84464-214">Get the current playback state of a recording.</span></span>

<span data-ttu-id="84464-215">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-215">Parameters</span></span>
* <span data-ttu-id="84464-216">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="84464-216">recording : Name of recording.</span></span>

<span data-ttu-id="84464-217">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="84464-217">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="84464-218">Выгрузить запись.</span><span class="sxs-lookup"><span data-stu-id="84464-218">Unload a recording.</span></span>

<span data-ttu-id="84464-219">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-219">Parameters</span></span>
* <span data-ttu-id="84464-220">запись: имя записи для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="84464-220">recording : Name of recording to unload.</span></span>

<span data-ttu-id="84464-221">**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-221">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="84464-222">Загрузка записи.</span><span class="sxs-lookup"><span data-stu-id="84464-222">Load a recording.</span></span>

<span data-ttu-id="84464-223">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-223">Parameters</span></span>
* <span data-ttu-id="84464-224">запись: имя загружаемой записи.</span><span class="sxs-lookup"><span data-stu-id="84464-224">recording : Name of recording to load.</span></span>

<span data-ttu-id="84464-225">**/АПИ/холографик/симулатион/плайбакк/Сессион/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-225">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="84464-226">Получение всех загруженных записей.</span><span class="sxs-lookup"><span data-stu-id="84464-226">Get all loaded recordings.</span></span>

<span data-ttu-id="84464-227">**/АПИ/холографик/симулатион/плайбакк/Сессион/паусе (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-227">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="84464-228">Приостановка записи.</span><span class="sxs-lookup"><span data-stu-id="84464-228">Pause a recording.</span></span>

<span data-ttu-id="84464-229">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-229">Parameters</span></span>
* <span data-ttu-id="84464-230">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="84464-230">recording : Name of recording.</span></span>

<span data-ttu-id="84464-231">**/АПИ/холографик/симулатион/плайбакк/Сессион/Плай (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-231">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="84464-232">Воспроизведение записи.</span><span class="sxs-lookup"><span data-stu-id="84464-232">Play a recording.</span></span>

<span data-ttu-id="84464-233">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-233">Parameters</span></span>
* <span data-ttu-id="84464-234">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="84464-234">recording : Name of recording.</span></span>

<span data-ttu-id="84464-235">**/АПИ/холографик/симулатион/плайбакк/Сессион/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-235">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="84464-236">Останавливает запись.</span><span class="sxs-lookup"><span data-stu-id="84464-236">Stop a recording.</span></span>

<span data-ttu-id="84464-237">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-237">Parameters</span></span>
* <span data-ttu-id="84464-238">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="84464-238">recording : Name of recording.</span></span>

<span data-ttu-id="84464-239">**/АПИ/холографик/симулатион/плайбакк/Сессион/типес (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-239">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="84464-240">Получение типов данных в загруженной записи.</span><span class="sxs-lookup"><span data-stu-id="84464-240">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="84464-241">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-241">Parameters</span></span>
* <span data-ttu-id="84464-242">запись: имя записи.</span><span class="sxs-lookup"><span data-stu-id="84464-242">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="84464-243">Запись имитации восприятия</span><span class="sxs-lookup"><span data-stu-id="84464-243">Perception Simulation Recording</span></span>

<span data-ttu-id="84464-244">**/АПИ/холографик/симулатион/рекординг/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-244">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="84464-245">Начать запись.</span><span class="sxs-lookup"><span data-stu-id="84464-245">Start a recording.</span></span> <span data-ttu-id="84464-246">Одновременно может быть активна только одна запись.</span><span class="sxs-lookup"><span data-stu-id="84464-246">Only a single recording can be active at once.</span></span> <span data-ttu-id="84464-247">Необходимо задать один из головок, «руки», «Спатиалмаппинг» или «среда».</span><span class="sxs-lookup"><span data-stu-id="84464-247">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="84464-248">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-248">Parameters</span></span>
* <span data-ttu-id="84464-249">Head: задайте значение 1, чтобы записать данные заголовка.</span><span class="sxs-lookup"><span data-stu-id="84464-249">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="84464-250">стрелки: значение 1, чтобы записать данные.</span><span class="sxs-lookup"><span data-stu-id="84464-250">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="84464-251">Спатиалмаппинг: задайте значение 1 для записи пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="84464-251">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="84464-252">окружение: задайте значение 1, чтобы записать данные среды.</span><span class="sxs-lookup"><span data-stu-id="84464-252">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="84464-253">имя. имя записи.</span><span class="sxs-lookup"><span data-stu-id="84464-253">name : Name of the recording.</span></span>
* <span data-ttu-id="84464-254">Синглеспатиалмаппингфраме: задайте значение 1, чтобы записать только один фрейм пространственного сопоставления.</span><span class="sxs-lookup"><span data-stu-id="84464-254">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="84464-255">**/АПИ/холографик/симулатион/рекординг/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-255">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="84464-256">Получение состояния записи.</span><span class="sxs-lookup"><span data-stu-id="84464-256">Get recording state.</span></span>

<span data-ttu-id="84464-257">**/АПИ/холографик/симулатион/рекординг/стоп (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-257">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="84464-258">Останавливает текущую запись.</span><span class="sxs-lookup"><span data-stu-id="84464-258">Stop the current recording.</span></span> <span data-ttu-id="84464-259">Запись будет возвращена в виде файла.</span><span class="sxs-lookup"><span data-stu-id="84464-259">Recording will be returned as a file.</span></span>

## <a name="mixed-reality-capture"></a><span data-ttu-id="84464-260">Смешанный захват реальности</span><span class="sxs-lookup"><span data-stu-id="84464-260">Mixed Reality Capture</span></span>

<span data-ttu-id="84464-261">**/АПИ/холографик/МРК/филе (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-261">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="84464-262">Скачивает файл смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="84464-262">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="84464-263">Use Op = потоковый параметр запроса для потоковой передачи.</span><span class="sxs-lookup"><span data-stu-id="84464-263">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="84464-264">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-264">Parameters</span></span>
* <span data-ttu-id="84464-265">имя файла: имя, hex64 в кодировке для получаемого видео.</span><span class="sxs-lookup"><span data-stu-id="84464-265">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="84464-266">Op: Stream</span><span class="sxs-lookup"><span data-stu-id="84464-266">op : stream</span></span>

<span data-ttu-id="84464-267">**/АПИ/холографик/МРК/филе (удаление)**</span><span class="sxs-lookup"><span data-stu-id="84464-267">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="84464-268">Удаляет запись смешанной реальности с устройства.</span><span class="sxs-lookup"><span data-stu-id="84464-268">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="84464-269">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-269">Parameters</span></span>
* <span data-ttu-id="84464-270">filename: Name, hex64 Encoded (имя файла), которое нужно удалить.</span><span class="sxs-lookup"><span data-stu-id="84464-270">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="84464-271">**/АПИ/холографик/МРК/Филес (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-271">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="84464-272">Возвращает список файлов смешанной реальности, хранящихся на устройстве</span><span class="sxs-lookup"><span data-stu-id="84464-272">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="84464-273">**/АПИ/холографик/МРК/фото (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-273">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="84464-274">Принимает фотографию смешанной реальности и создает файл на устройстве</span><span class="sxs-lookup"><span data-stu-id="84464-274">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="84464-275">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-275">Parameters</span></span>
* <span data-ttu-id="84464-276">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="84464-276">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="84464-277">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="84464-277">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="84464-278">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="84464-278">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="84464-279">**/АПИ/холографик/МРК/Сеттингс (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-279">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="84464-280">Получает параметры записи смешанной реальности по умолчанию</span><span class="sxs-lookup"><span data-stu-id="84464-280">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="84464-281">**/АПИ/холографик/МРК/Сеттингс (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-281">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="84464-282">Задает параметры записи смешанной реальности по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="84464-282">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="84464-283">Некоторые из этих параметров применяются к фотографии и видеозаписи системы требований к системе.</span><span class="sxs-lookup"><span data-stu-id="84464-283">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="84464-284">**/АПИ/холографик/МРК/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-284">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="84464-285">Возвращает состояние записанной смешанной реальности (запущена, остановлена)</span><span class="sxs-lookup"><span data-stu-id="84464-285">Gets the status of the mixed reality recorded (running, stopped)</span></span>

<span data-ttu-id="84464-286">**/АПИ/холографик/МРК/сумбнаил (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-286">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="84464-287">Получает эскиз изображения для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="84464-287">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="84464-288">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-288">Parameters</span></span>
* <span data-ttu-id="84464-289">filename: Name, hex64 Encoded, файла, для которого запрашивается эскиз.</span><span class="sxs-lookup"><span data-stu-id="84464-289">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="84464-290">**/АПИ/холографик/МРК/видео/контрол/старт (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-290">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="84464-291">Запуск записи смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="84464-291">Starts a mixed reality recording</span></span>

<span data-ttu-id="84464-292">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-292">Parameters</span></span>
* <span data-ttu-id="84464-293">Холо: голограммы захвата: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="84464-293">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="84464-294">ПС: захват ПС Camera: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="84464-294">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="84464-295">MIC: записать микрофон: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="84464-295">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="84464-296">замыкание на себя: запись звука приложения: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="84464-296">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="84464-297">Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="84464-297">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="84464-298">встаб: (только HoloLens 2) Enable Video стабилизации: true или false (значение по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="84464-298">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="84464-299">встаббуффер: (только HoloLens 2) задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="84464-299">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="84464-300">**/АПИ/холографик/МРК/видео/контрол/стоп (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-300">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="84464-301">Останавливает текущую запись смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="84464-301">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="84464-302">Потоковая передача смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="84464-302">Mixed Reality Streaming</span></span>

<span data-ttu-id="84464-303">HoloLens поддерживает динамическую предварительную версию смешанной реальности через частную загрузку фрагментированного MP4.</span><span class="sxs-lookup"><span data-stu-id="84464-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="84464-304">Потоки смешанной реальности используют один и тот же набор параметров для управления тем, что захватывается:</span><span class="sxs-lookup"><span data-stu-id="84464-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="84464-305">Холо: голограммы записи: true или false</span><span class="sxs-lookup"><span data-stu-id="84464-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="84464-306">ПС: запись камеры PV: true или false</span><span class="sxs-lookup"><span data-stu-id="84464-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="84464-307">микрофон: записать микрофон: true или false</span><span class="sxs-lookup"><span data-stu-id="84464-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="84464-308">замыкание на себя: запись звука приложения: true или false</span><span class="sxs-lookup"><span data-stu-id="84464-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="84464-309">Если ни один из этих элементов не указан: будут записываться голограммы, Фото-и видеокамера и звук приложения</span><span class="sxs-lookup"><span data-stu-id="84464-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="84464-310">Если таковые имеются, то по умолчанию для неуказанных параметров будет задано значение false.</span><span class="sxs-lookup"><span data-stu-id="84464-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="84464-311">Необязательные параметры (только HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="84464-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="84464-312">Рендерфромкамера: прорисовка с точки зрения фотографии или видеокамеры: true или false (по умолчанию — true)</span><span class="sxs-lookup"><span data-stu-id="84464-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="84464-313">встаб: enable Video стабилизации: true или false (по умолчанию — false)</span><span class="sxs-lookup"><span data-stu-id="84464-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="84464-314">встаббуффер: задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)</span><span class="sxs-lookup"><span data-stu-id="84464-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="84464-315">**/API/holographic/Stream/Live.MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="84464-316">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="84464-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="84464-317">**/АПИ/холографик/стреам/live_high. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="84464-318">1280x720p 30fps 5Mbit Stream.</span><span class="sxs-lookup"><span data-stu-id="84464-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="84464-319">**/АПИ/холографик/стреам/live_med. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="84464-320">Поток 854x480p 30fps 2.5 Мбит.</span><span class="sxs-lookup"><span data-stu-id="84464-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="84464-321">**/АПИ/холографик/стреам/live_low. MP4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="84464-322">Поток 428x240p 15fps 0,6 Мбит.</span><span class="sxs-lookup"><span data-stu-id="84464-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="84464-323">Сеть</span><span class="sxs-lookup"><span data-stu-id="84464-323">Networking</span></span>

<span data-ttu-id="84464-324">**/АПИ/нетворкинг/ипконфиг (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="84464-325">Возвращает текущую IP-конфигурацию</span><span class="sxs-lookup"><span data-stu-id="84464-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="84464-326">Сведения о ОС</span><span class="sxs-lookup"><span data-stu-id="84464-326">OS Information</span></span>

<span data-ttu-id="84464-327">**/АПИ/ОС/Инфо (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="84464-328">Получение сведений об операционной системе</span><span class="sxs-lookup"><span data-stu-id="84464-328">Gets operating system information</span></span>

<span data-ttu-id="84464-329">**/АПИ/ОС/мачиненаме (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="84464-330">Возвращает имя компьютера.</span><span class="sxs-lookup"><span data-stu-id="84464-330">Gets the machine name</span></span>

<span data-ttu-id="84464-331">**/АПИ/ОС/мачиненаме (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="84464-332">Задает имя компьютера</span><span class="sxs-lookup"><span data-stu-id="84464-332">Sets the machine name</span></span>

<span data-ttu-id="84464-333">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-333">Parameters</span></span>
* <span data-ttu-id="84464-334">Имя: новое имя компьютера, hex64 в кодировке, для которого задано значение.</span><span class="sxs-lookup"><span data-stu-id="84464-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="performance-data"></a><span data-ttu-id="84464-335">Данные о производительности</span><span class="sxs-lookup"><span data-stu-id="84464-335">Performance data</span></span>

<span data-ttu-id="84464-336">**/АПИ/ресаурцеманажер/процессес (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-336">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="84464-337">Возвращает список запущенных процессов с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="84464-337">Returns the list of running processes with details</span></span>

<span data-ttu-id="84464-338">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-338">Return data</span></span>
* <span data-ttu-id="84464-339">JSON со списком процессов и сведений для каждого процесса</span><span class="sxs-lookup"><span data-stu-id="84464-339">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="84464-340">**/АПИ/ресаурцеманажер/системперф (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-340">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="84464-341">Возвращает статистику производительности системы (операции чтения и записи ввода-вывода, статистика памяти и т. д.).</span><span class="sxs-lookup"><span data-stu-id="84464-341">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="84464-342">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-342">Return data</span></span>
* <span data-ttu-id="84464-343">JSON со сведениями о системе: ЦП, GPU, память, сеть, IO</span><span class="sxs-lookup"><span data-stu-id="84464-343">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="84464-344">Power</span><span class="sxs-lookup"><span data-stu-id="84464-344">Power</span></span>

<span data-ttu-id="84464-345">**/АПИ/повер/Баттери (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-345">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="84464-346">Возвращает текущее состояние аккумулятора</span><span class="sxs-lookup"><span data-stu-id="84464-346">Gets the current battery state</span></span>

<span data-ttu-id="84464-347">**/АПИ/повер/Стате (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-347">**/api/power/state (GET)**</span></span>

<span data-ttu-id="84464-348">Проверяет, находится ли система в состоянии с низким энергопотреблением</span><span class="sxs-lookup"><span data-stu-id="84464-348">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="84464-349">Удаленное управление</span><span class="sxs-lookup"><span data-stu-id="84464-349">Remote Control</span></span>

<span data-ttu-id="84464-350">**/АПИ/контрол/рестарт (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-350">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="84464-351">Перезапускает целевое устройство</span><span class="sxs-lookup"><span data-stu-id="84464-351">Restarts the target device</span></span>

<span data-ttu-id="84464-352">**/АПИ/контрол/шутдовн (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-352">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="84464-353">Завершает работу целевого устройства</span><span class="sxs-lookup"><span data-stu-id="84464-353">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="84464-354">Диспетчер задач</span><span class="sxs-lookup"><span data-stu-id="84464-354">Task Manager</span></span>

<span data-ttu-id="84464-355">**/АПИ/таскманажер/АПП (удаление)**</span><span class="sxs-lookup"><span data-stu-id="84464-355">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="84464-356">Останавливает современное приложение</span><span class="sxs-lookup"><span data-stu-id="84464-356">Stops a modern app</span></span>

<span data-ttu-id="84464-357">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-357">Parameters</span></span>
* <span data-ttu-id="84464-358">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="84464-358">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="84464-359">форцестоп: принудительно останавливаются все процессы (= да)</span><span class="sxs-lookup"><span data-stu-id="84464-359">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="84464-360">**/АПИ/таскманажер/АПП (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-360">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="84464-361">Запуск современного приложения</span><span class="sxs-lookup"><span data-stu-id="84464-361">Starts a modern app</span></span>

<span data-ttu-id="84464-362">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-362">Parameters</span></span>
* <span data-ttu-id="84464-363">AppID: ПРАИД приложения для запуска, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="84464-363">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="84464-364">Package: полное имя пакета приложения, hex64 в кодировке</span><span class="sxs-lookup"><span data-stu-id="84464-364">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="84464-365">Управление Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="84464-365">WiFi Management</span></span>

<span data-ttu-id="84464-366">**/АПИ/ВИФИ/интерфацес (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-366">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="84464-367">Перечисляет беспроводные сетевые интерфейсы</span><span class="sxs-lookup"><span data-stu-id="84464-367">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="84464-368">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-368">Return data</span></span>
* <span data-ttu-id="84464-369">Список беспроводных интерфейсов с подробными сведениями (GUID, описание и т. д.).</span><span class="sxs-lookup"><span data-stu-id="84464-369">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="84464-370">**/АПИ/ВИФИ/Нетворк (удаление)**</span><span class="sxs-lookup"><span data-stu-id="84464-370">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="84464-371">Удаление профиля, связанного с сетью, в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="84464-371">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="84464-372">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-372">Parameters</span></span>
* <span data-ttu-id="84464-373">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="84464-373">interface : network interface guid</span></span>
* <span data-ttu-id="84464-374">Профиль: имя профиля</span><span class="sxs-lookup"><span data-stu-id="84464-374">profile : profile name</span></span>

<span data-ttu-id="84464-375">**/АПИ/ВИФИ/Нетворкс (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-375">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="84464-376">Перечисляет беспроводные сети в указанном сетевом интерфейсе</span><span class="sxs-lookup"><span data-stu-id="84464-376">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="84464-377">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-377">Parameters</span></span>
* <span data-ttu-id="84464-378">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="84464-378">interface : network interface guid</span></span>

<span data-ttu-id="84464-379">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-379">Return data</span></span>
* <span data-ttu-id="84464-380">Список беспроводных сетей, обнаруженных в сетевом интерфейсе, с подробными сведениями</span><span class="sxs-lookup"><span data-stu-id="84464-380">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="84464-381">**/АПИ/ВИФИ/Нетворк (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-381">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="84464-382">Подключение к сети или отключение от него по указанному интерфейсу</span><span class="sxs-lookup"><span data-stu-id="84464-382">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="84464-383">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-383">Parameters</span></span>
* <span data-ttu-id="84464-384">интерфейс: GUID сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="84464-384">interface : network interface guid</span></span>
* <span data-ttu-id="84464-385">SSID: SSID, hex64 в кодировке для подключения</span><span class="sxs-lookup"><span data-stu-id="84464-385">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="84464-386">Операция: подключение или отключение</span><span class="sxs-lookup"><span data-stu-id="84464-386">op : connect or disconnect</span></span>
* <span data-ttu-id="84464-387">креатепрофиле: Да или нет</span><span class="sxs-lookup"><span data-stu-id="84464-387">createprofile : yes or no</span></span>
* <span data-ttu-id="84464-388">ключ: Shared Key, hex64 Encoded</span><span class="sxs-lookup"><span data-stu-id="84464-388">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="84464-389">Средство записи производительности Windows</span><span class="sxs-lookup"><span data-stu-id="84464-389">Windows Performance Recorder</span></span>

<span data-ttu-id="84464-390">**/АПИ/ВПР/кустомтраце (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-390">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="84464-391">Отправляет профиль ЗВЧ и начинает трассировку с помощью отправленного профиля.</span><span class="sxs-lookup"><span data-stu-id="84464-391">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="84464-392">Полезные данные</span><span class="sxs-lookup"><span data-stu-id="84464-392">Payload</span></span>
* <span data-ttu-id="84464-393">текст HTTP из нескольких частей</span><span class="sxs-lookup"><span data-stu-id="84464-393">multi-part conforming http body</span></span>

<span data-ttu-id="84464-394">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-394">Return data</span></span>
* <span data-ttu-id="84464-395">Возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="84464-395">Returns the WPR session status.</span></span>

<span data-ttu-id="84464-396">**/АПИ/ВПР/статус (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-396">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="84464-397">Получение состояния сеанса ЗВЧ</span><span class="sxs-lookup"><span data-stu-id="84464-397">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="84464-398">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-398">Return data</span></span>
* <span data-ttu-id="84464-399">Состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="84464-399">WPR session status.</span></span>

<span data-ttu-id="84464-400">**/АПИ/ВПР/траце (GET)**</span><span class="sxs-lookup"><span data-stu-id="84464-400">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="84464-401">Останавливает сеанс трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="84464-401">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="84464-402">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-402">Return data</span></span>
* <span data-ttu-id="84464-403">Возвращает ETL-файл трассировки</span><span class="sxs-lookup"><span data-stu-id="84464-403">Returns the trace ETL file</span></span>

<span data-ttu-id="84464-404">**/АПИ/ВПР/траце (POST)**</span><span class="sxs-lookup"><span data-stu-id="84464-404">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="84464-405">Запускает сеансы трассировки ЗВЧ (производительность)</span><span class="sxs-lookup"><span data-stu-id="84464-405">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="84464-406">Параметры</span><span class="sxs-lookup"><span data-stu-id="84464-406">Parameters</span></span>
* <span data-ttu-id="84464-407">Профиль: имя профиля.</span><span class="sxs-lookup"><span data-stu-id="84464-407">profile : Profile name.</span></span> <span data-ttu-id="84464-408">Доступные профили хранятся в перфпрофилес/Profiles. JSON.</span><span class="sxs-lookup"><span data-stu-id="84464-408">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="84464-409">Возвращать данные</span><span class="sxs-lookup"><span data-stu-id="84464-409">Return data</span></span>
* <span data-ttu-id="84464-410">При запуске возвращает состояние сеанса ЗВЧ.</span><span class="sxs-lookup"><span data-stu-id="84464-410">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="84464-411">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="84464-411">See also</span></span>
* [<span data-ttu-id="84464-412">Использование портала устройств Windows</span><span class="sxs-lookup"><span data-stu-id="84464-412">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="84464-413">Справочник по API для базовых порталов устройств (UWP)</span><span class="sxs-lookup"><span data-stu-id="84464-413">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
