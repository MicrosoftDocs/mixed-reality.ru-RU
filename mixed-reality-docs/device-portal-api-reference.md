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
# <a name="device-portal-api-reference"></a>Портал устройств Справочник по API

Все, что в [Windows Device Portal](using-the-windows-device-portal.md) построена на основе REST API можно использовать для доступа к данным и управления устройства программными средствами.

## <a name="app-deloyment"></a>С развертыванием приложений

**/API/App/packagemanager/Package (удаление)**

Удаляет приложение

Параметры
* пакет: Имя файла пакета, который требуется удалить.

**/API/App/packagemanager/Package (POST)**

Устанавливает приложение

Параметры
* пакет: Имя файла пакета должны быть установлены.

полезные данные
* составной согласование основного текста http

**/API/App/packagemanager/Packages (GET)**

Извлекает список установленных приложений в системе, с подробными сведениями

Возвращаемые данные
* Список установленных пакетов с подробными сведениями

**/API/App/packagemanager/State (GET)**

Возвращает состояние хода выполнения установки приложения

## <a name="dump-collection"></a>Коллекция дампов

**/API/Debug/Dump/Usermode/CrashControl (удаление)**

Отключает сбор аварийных дампов для загрузка неопубликованного приложения

Параметры
* "полноеимяпакета": имя пакета

**/API/Debug/Dump/Usermode/CrashControl (GET)**

Возвращает параметры для неопубликованных приложений сбора аварийных дампов

Параметры
* "полноеимяпакета": имя пакета

**/API/Debug/Dump/Usermode/CrashControl (POST)**

Включает и задает параметры управления дампа для загрузка неопубликованного приложения

Параметры
* "полноеимяпакета": имя пакета

**/API/Debug/Dump/Usermode/crashdump (удаление)**

Удаляет дампа для загрузка неопубликованного приложения

Параметры
* "полноеимяпакета": имя пакета
* Имя файла: имя файла дампа

**/API/Debug/Dump/Usermode/crashdump (GET)**

Извлекает дампа для загрузка неопубликованного приложения

Параметры
* "полноеимяпакета": имя пакета
* Имя файла: имя файла дампа

Возвращаемые данные
* Файл дампа. Проверить с помощью Visual Studio или WinDbg

**/API/Debug/Dump/Usermode/dumps (GET)**

Возвращает список всех аварийных дампов для неопубликованных приложений

Возвращаемые данные
* Список аварийных дампов на стороне загрузить приложение

## <a name="etw"></a>Трассировка событий Windows

**/API/ETW/Providers (GET)**

Перечисляет зарегистрированных поставщиков

Возвращаемые данные
* Список поставщиков, понятное имя и идентификатор GUID

**/API/ETW/Session/RealTime (GET и WebSocket)**

Создает сеанс трассировки событий Windows в реальном времени; управлять через websocket.

Возвращаемые данные
* События трассировки событий Windows из разрешенных поставщиков

## <a name="holographic-os"></a>Holographic OS

**/API/holographic/OS/ETW/customproviders (GET)**

Возвращает список поставщиков трассировки событий Windows конкретного HoloLens, которые не зарегистрированы в системе

**/API/holographic/OS/Services (GET)**

Возвращает состояния всех служб, запущенных.

**/API/holographic/OS/Settings/IPD (GET)**

Возвращает хранимые IPD (Interpupillary расстояние) в миллиметрах

**/API/holographic/OS/Settings/IPD (POST)**

Задает IPD

Параметры
* IPD: Новое значение IPD, задаваемый в миллиметрах

**/API/holographic/OS/webmanagement/Settings/HTTPS (GET)**

Получение требований HTTPS для Портала устройств

**/API/holographic/OS/webmanagement/Settings/HTTPS (POST)**

Задает требования к HTTPS для портала устройства

Параметры
* требуется: yes, нет или значение по умолчанию

## <a name="holographic-perception"></a>Holographic восприятие

**/API/holographic/perception/Client (GET и WebSocket)**

Принимает обновления websocket и запускает восприятие клиента, который отправляет обновления 30 кадров в секунду.

Параметры
* clientmode: «активно» принудительно включает режим visual отслеживания при его не удается установить пассивно

## <a name="holographic-thermal"></a>Температурное holographic

**/API/holographic/Thermal/Stage (GET)**

Получить температуры рабочей области устройства (обычный 0, 1 "горячего" резервирования, критические 2)

## <a name="perception-simulation-control"></a>Элемент управления моделирования восприятие

**/API/holographic/Simulation/Control/Mode (GET)**

Получение режима моделирования

**/API/holographic/Simulation/Control/Mode (POST)**

Установить режим моделирования

Параметры
* режим: режиме моделирования: по умолчанию, моделирование, удаленное, прежних версий

**/API/holographic/Simulation/Control/Stream (удаление)**

Удалите поток управления.

**/API/holographic/Simulation/Control/Stream (GET и WebSocket)**

Откройте подключение веб-сокета для потока управления.

**/API/holographic/Simulation/Control/Stream (POST)**

Создание потока управления (приоритетом является обязательным) или отправки данных в созданный потока (streamId требуется). Переданные данные должен иметь тип «application/octet-stream».

## <a name="perception-simulation-playback"></a>Воспроизведение моделирования восприятие

**/API/holographic/Simulation/Playback/File (удаление)**

Удаление записи.

Параметры
* запись: Имя записи для удаления.

**/API/holographic/Simulation/Playback/File (POST)**

Отправьте запись.

**/API/holographic/Simulation/Playback/Files (GET)**

Получение всех записей.

**/API/holographic/Simulation/Playback/Session (GET)**

Получите текущее состояние воспроизведения записи.

Параметры
* запись: Имя записи.

**/API/holographic/Simulation/Playback/Session/File (удаление)**

Выгрузите операцию записи.

Параметры
* запись: Имя записи для выгрузки.

**/API/holographic/Simulation/Playback/Session/File (POST)**

Загрузите записи.

Параметры
* запись: Имя записи для загрузки.

**/API/holographic/Simulation/Playback/Session/Files (GET)**

Получение всех загруженных записей.

**/API/holographic/Simulation/Playback/Session/Pause (POST)**

Приостановите запись.

Параметры
* запись: Имя записи.

**/API/holographic/Simulation/Playback/Session/Play (POST)**

Воспроизвести.

Параметры
* запись: Имя записи.

**/API/holographic/Simulation/Playback/Session/Stop (POST)**

Остановите запись.

Параметры
* запись: Имя записи.

**/API/holographic/Simulation/Playback/Session/Types (GET)**

Получите типы данных во время загрузки записи.

Параметры
* запись: Имя записи.

## <a name="perception-simulation-recording"></a>Запись моделирования восприятие

**/API/holographic/Simulation/Recording/Start (POST)**

Начните запись. Только одной записи могут быть активны одновременно. Должно быть задано одно из head, руки, spatialMapping или среды.

Параметры
* головной узел: Значение 1 для головного данные записи.
* Практическое. Значение 1 для записи данных вручную.
* spatialMapping: Значение 1 для записи пространственное сопоставление.
* Среда: Значение 1 для записи данных в среде.
* Имя: Имя записи.
* singleSpatialMappingFrame: Значение 1 для записи только одно сопоставление пространственных кадра.

**/API/holographic/Simulation/Recording/Status (GET)**

Получить запись состояния.

**/API/holographic/Simulation/Recording/Stop (GET)**

Остановите текущую запись. Запись будет возвращаться в виде файла.

## <a name="mixed-reality-capture"></a>Смешанный захват реальности

**/API/holographic/MRC/File (GET)**

Загружает файл смешанной реальности из устройства. Используйте op = параметр запроса потока для потоковой передачи.

Параметры
* Имя файла: Имя, hex64, кодирования видео для получения файла
* op: поток

**/API/holographic/MRC/File (удаление)**

Удаляет смешанной реальности, записи с устройства.

Параметры
* Имя файла: Имя, hex64 кодировке файла для удаления

**/API/holographic/MRC/Files (GET)**

Возвращает список файлов смешанной реальности, хранящихся на устройстве

**/API/holographic/MRC/Photo (POST)**

Делает снимок смешанной реальности и создает файл на устройстве

Параметры
* holo: захват голограммы: true или false (по умолчанию — false)
* PV: записи PV камеры: true или false (по умолчанию — false)
* RenderFromCamera: Отрисовки (только для HoloLens 2) с точки зрения камеры фото и видео: true или false (по умолчанию — true)

**/API/holographic/MRC/Settings (GET)**

Получает значение по умолчанию смешанной реальности параметры записи

**/API/holographic/MRC/Settings (POST)**

Задает значение по умолчанию смешанной реальности параметры записи.  Некоторые из этих параметров применяются к фотографии MRC системы и видеозаписи.

**/API/holographic/MRC/Status (GET)**

Возвращает состояние смешанной реальности записи ("выполняется", "Остановлено")

**/API/holographic/MRC/Thumbnail (GET)**

Возвращает эскиз для указанного файла.

Параметры
* Имя файла: Имя, hex64 в кодировке, для которого запрашивается эскиза файла

**/API/holographic/MRC/Video/Control/Start (POST)**

Запускает запись смешанной реальности

Параметры
* holo: захват голограммы: true или false (по умолчанию — false)
* PV: записи PV камеры: true или false (по умолчанию — false)
* MIC: "микрофон" захвата: true или false (по умолчанию — false)
* замыкания на себя: запись звука приложения: true или false (по умолчанию — false)
* RenderFromCamera: Отрисовки (только для HoloLens 2) с точки зрения камеры фото и видео: true или false (по умолчанию — true)
* vstab: Стабилизации видео enable (только для HoloLens 2): true или false (по умолчанию — true)
* vstabbuffer: Задержка буфера стабилизации видео (только для HoloLens 2): 0 до 30 кадров (по умолчанию — 15 кадров)

**/API/holographic/MRC/Video/Control/Stop (POST)**

Останавливает текущий смешанный записи реальность

## <a name="mixed-reality-streaming"></a>Смешанная реальность потоковой передачи

HoloLens поддерживает интерактивный просмотр смешанной реальности через фрагментированный загрузки фрагментированного mp4.

Смешанная реальность потоки совместно используют тот же набор параметров для управления, что записывается:
* holo: захват голограммы: true или false
* PV: записи PV камеры: true или false
* MIC: "микрофон" захвата: true или false
* замыкания на себя: запись звука приложения: true или false

Если не указан ни один из них: голограммы камеры фото и видео и аудио приложения будут записаны<br>
Если указаны какие: Незаданные параметры по умолчанию используется значение false

Необязательные параметры (только для HoloLens 2)
* RenderFromCamera: отрисовки с точки зрения камеры фото и видео: true или false (по умолчанию — true)
* vstab: включить стабилизации видео: true или false (по умолчанию — false)
* vstabbuffer: задержка буфера стабилизации видео: 0 до 30 кадров (по умолчанию — 15 кадров)

**/API/holographic/Stream/Live.MP4 (GET)**

Поток 5Mbit 1280x720p 30 кадров/с.

**/API/holographic/Stream/live_high.MP4 (GET)**

Поток 5Mbit 1280x720p 30 кадров/с.

**/API/holographic/Stream/live_med.MP4 (GET)**

Поток 854x480p 2.5Mbit 30 кадров/с.

**/API/holographic/Stream/live_low.MP4 (GET)**

Поток 428x240p 0.6Mbit 15 кадров/с.

## <a name="networking"></a>Сеть

**/API/Networking/ipconfig (GET)**

Возвращает текущую конфигурацию IP-адрес

## <a name="os-information"></a>Данные о ОС

**/API/OS/Info (GET)**

Возвращает сведения об операционной системе

**/API/OS/MachineName (GET)**

Получает имя компьютера

**/API/OS/MachineName (POST)**

Задает имя компьютера

Параметры
* Имя: Новое имя компьютера, hex64 в кодировке, присвоено значение

## <a name="performance-data"></a>Данные о производительности

**/API/ResourceManager/Processes (GET)**

Возвращает список выполняющихся процессов с подробными сведениями

Возвращаемые данные
* JSON с помощью списка процессов и сведения для каждого процесса

**/API/ResourceManager/systemperf (GET)**

Возвращает статистику производительности системы (операций ввода-вывода чтения и записи, Статистика использования памяти и т.д.

Возвращаемые данные
* JSON с помощью сведений о системе: ЦП, графического Процессора, памяти, сети, операции ввода-ВЫВОДА

## <a name="power"></a>Питание

**/API/Power/Battery (GET)**

Возвращает текущее состояние батареи

**/API/Power/State (GET)**

Проверяет, находится ли система в состоянии пониженного энергопотребления

## <a name="remote-control"></a>Удаленное управление

**/API/Control/Restart (POST)**

Перезапускает целевого устройства

**/API/Control/Shutdown (POST)**

Завершает работу целевого устройства

## <a name="task-manager"></a>Диспетчер задач

**/API/TaskManager/App (удаление)**

Останавливает современных приложений

Параметры
* пакет: Полное имя пакета приложения, hex64 кодировке
* forcestop: Принудительно все процессы, чтобы остановить (= Да)

**/API/TaskManager/App (POST)**

Запускает современных приложений

Параметры
* AppID: В кодировке hex64 PRAID приложения для запуска
* пакет: Полное имя пакета приложения, hex64 кодировке

## <a name="wifi-management"></a>Управление Wi-Fi

**/API/WiFi/Interfaces (GET)**

Перечисляет беспроводных сетевых интерфейсов

Возвращаемые данные
* Список беспроводных интерфейсах с подробными сведениями (идентификатор GUID, описание и т.д.)

**/API/WiFi/Network (удаление)**

Удаление профиля, связанные с сетью для указанного интерфейса

Параметры
* интерфейс: сетевой интерфейс guid
* профиль: имя профиля

**/API/WiFi/Networks (GET)**

Перечисляет беспроводных сетей на указанного сетевого интерфейса

Параметры
* интерфейс: сетевой интерфейс guid

Возвращаемые данные
* Список беспроводных сетей, найденных на интерфейсе с подробными сведениями

**/API/WiFi/Network (POST)**

Подключении или отключении сети для указанного интерфейса

Параметры
* интерфейс: сетевой интерфейс guid
* SSID: ssid, hex64 в кодировке, для подключения к
* op: подключение и отключение
* CreateProfile: Да или нет
* ключ: общего ключа, hex64 кодировке

## <a name="windows-performance-recorder"></a>Средство записи производительности Windows

**/API/wpr/customtrace (POST)**

Передает WPR профиль и запускает трассировку с помощью загруженного профиля.

полезные данные
* составной согласование основного текста http

Возвращаемые данные
* Возвращает состояние сеанса WPR.

**/API/wpr/Status (GET)**

Получает сведения о состоянии сеанса WPR

Возвращаемые данные
* Состояние сеанса в WPR.

**/API/wpr/trace (GET)**

Останавливает сеанс трассировки WPR (производительность)

Возвращаемые данные
* Возвращает ETL-файла трассировки

**/API/wpr/trace (POST)**

Запускает WPR (производительность), отслеживание сеансов

Параметры
* профиль: Имя профиля. Доступные профили хранятся в perfprofiles/profiles.json

Возвращаемые данные
* При запуске возвращает состояние сеанса WPR.

## <a name="see-also"></a>См. также
* [Использование портала устройств Windows](using-the-windows-device-portal.md)
* [Core портала устройства Справочник по API (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
