---
title: Справочник по API портала устройств
description: Справочник по API для портала устройств Windows на HoloLens
author: hamalawi
ms.author: moelhama
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, портал устройств Windows, API
ms.openlocfilehash: b9b9ada49b4f9810dc97c9da2873d4ccb60df424
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441801"
---
# <a name="device-portal-api-reference"></a>Справочник по API портала устройств

Все на [портале устройств Windows](using-the-windows-device-portal.md) основаны на REST API, которые можно использовать для программного доступа к данным и управления устройством.

## <a name="app-deloyment"></a>Развертывании приложения

**/АПИ/АПП/паккажеманажер/паккаже (удаление)**

Удаляет приложение.

Параметры
* Пакет: имя файла удаляемого пакета.

**/АПИ/АПП/паккажеманажер/паккаже (POST)**

Устанавливает приложение

Параметры
* Пакет: имя файла устанавливаемого пакета.

Полезные данные
* текст HTTP из нескольких частей

**/АПИ/АПП/паккажеманажер/паккажес (GET)**

Извлекает список установленных приложений в системе со сведениями

Возвращать данные
* Список установленных пакетов со сведениями

**/АПИ/АПП/паккажеманажер/Стате (GET)**

Возвращает состояние выполняющейся установки приложения.

## <a name="dump-collection"></a>Дамп коллекции

**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (удаление)**

Отключает сбор аварийных дампов для приложения загруженные неопубликованные

Параметры
* Полноеимяпакета: имя пакета

**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (GET)**

Получение параметров для коллекции аварийных дампов приложений загруженные неопубликованные

Параметры
* Полноеимяпакета: имя пакета

**/АПИ/дебуг/ДУМП/усермоде/крашконтрол (POST)**

Включает и задает параметры управления дампом для приложения загруженные неопубликованные

Параметры
* Полноеимяпакета: имя пакета

**/АПИ/дебуг/ДУМП/усермоде/крашдумп (удаление)**

Удаляет аварийный дамп для приложения загруженные неопубликованные

Параметры
* Полноеимяпакета: имя пакета
* имя_файла: имя файла дампа

**/АПИ/дебуг/ДУМП/усермоде/крашдумп (GET)**

Получает аварийный дамп для приложения загруженные неопубликованные

Параметры
* Полноеимяпакета: имя пакета
* имя_файла: имя файла дампа

Возвращать данные
* Файл дампа. Проверка с помощью WinDbg или Visual Studio

**/АПИ/дебуг/ДУМП/усермоде/думпс (GET)**

Возвращает список всех аварийных дампов для приложений загруженные неопубликованные

Возвращать данные
* Список аварийных дампов для приложения, загруженного на стороне

## <a name="etw"></a>Трассировка событий Windows

**/АПИ/ЕТВ/провидерс (GET)**

Перечисляет зарегистрированные поставщики

Возвращать данные
* Список поставщиков, понятное имя и идентификатор GUID

**/АПИ/ЕТВ/Сессион/реалтиме (GET/WebSocket)**

Создает сеанс ETW в режиме реального времени; управляется через WebSocket.

Возвращать данные
* События ETW из включенных поставщиков

## <a name="holographic-os"></a>Holographic OS

**/АПИ/холографик/ОС/ЕТВ/кустомпровидерс (GET)**

Возвращает список поставщиков ETW, которые не зарегистрированы в системе.

**/АПИ/холографик/ОС/сервицес (GET)**

Возвращает состояния всех служб, на которых выполняются службы.

**/АПИ/холографик/ОС/Сеттингс/ИПД (GET)**

Получает хранимую IPD (Интерпупиллари distance) в миллиметрах

**/АПИ/холографик/ОС/Сеттингс/ИПД (POST)**

Задает IPD

Параметры
* IPD: новое значение IPD для установки в миллиметрах

**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (GET)**

Получение требований HTTPS для Портала устройств

**/АПИ/холографик/ОС/вебманажемент/Сеттингс/хттпс (POST)**

Установка требований HTTPS для портала устройств

Параметры
* обязательный: Да, нет или по умолчанию

## <a name="holographic-perception"></a>Holographic восприятие

**/АПИ/холографик/перцептион/клиент (GET/WebSocket)**

Принимает обновления WebSocket и запускает клиент-восприятие, которое отправляет обновления с частотой 30 кадров/с.

Параметры
* клиентмоде: "Active" запускает режим отслеживания визуального элемента, если он не может быть установлен в пассивном режиме

## <a name="holographic-thermal"></a>Голограмма holographic

**/АПИ/холографик/сермал/стаже (GET)**

Получите температурный этап устройства (0 нормальная, 1 тепло, 2 критическая)

## <a name="perception-simulation-control"></a>Элемент управления имитацией восприятия

**/АПИ/холографик/симулатион/контрол/моде (GET)**

Получение режима моделирования

**/АПИ/холографик/симулатион/контрол/моде (POST)**

Установка режима имитации

Параметры
* режим: режим имитации: по умолчанию, имитация, удаленный, устаревший

**/АПИ/холографик/симулатион/контрол/стреам (удаление)**

Удаляет поток управления.

**/АПИ/холографик/симулатион/контрол/стреам (GET/WebSocket)**

Откройте подключение к веб-сокету для потока управления.

**/АПИ/холографик/симулатион/контрол/стреам (POST)**

Создайте поток управления (требуется приоритет) или опубликуйте данные в созданном потоке (требуется streamId). Ожидаемые данные должны иметь тип "Application/октет-Stream".

**/АПИ/холографик/симулатион/дисплай/стреам (GET/WebSocket)**

Запросите поток видео имитации, содержащий содержимое, отображаемое для отображения в системе, в режиме "имитация".  Сначала будет отправлен заголовок простого дескриптора формата, а затем H. 264-Encoded текстуры, в каждой из которых предшествует заголовок, указывающий индекс глаза и размер текстуры.

## <a name="perception-simulation-playback"></a>Воспроизведение имитации восприятия

**/АПИ/холографик/симулатион/плайбакк/филе (удаление)**

Удаление записи.

Параметры
* запись: имя записи для удаления.

**/АПИ/холографик/симулатион/плайбакк/филе (POST)**

Отправьте запись.

**/АПИ/холографик/симулатион/плайбакк/Филес (GET)**

Получение всех записей.

**/АПИ/холографик/симулатион/плайбакк/Сессион (GET)**

Получение текущего состояния воспроизведения записи.

Параметры
* запись: имя записи.

**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (удаление)**

Выгрузить запись.

Параметры
* запись: имя записи для выгрузки.

**/АПИ/холографик/симулатион/плайбакк/Сессион/филе (POST)**

Загрузка записи.

Параметры
* запись: имя загружаемой записи.

**/АПИ/холографик/симулатион/плайбакк/Сессион/Филес (GET)**

Получение всех загруженных записей.

**/АПИ/холографик/симулатион/плайбакк/Сессион/паусе (POST)**

Приостановка записи.

Параметры
* запись: имя записи.

**/АПИ/холографик/симулатион/плайбакк/Сессион/Плай (POST)**

Воспроизведение записи.

Параметры
* запись: имя записи.

**/АПИ/холографик/симулатион/плайбакк/Сессион/стоп (POST)**

Останавливает запись.

Параметры
* запись: имя записи.

**/АПИ/холографик/симулатион/плайбакк/Сессион/типес (GET)**

Получение типов данных в загруженной записи.

Параметры
* запись: имя записи.

## <a name="perception-simulation-recording"></a>Запись имитации восприятия

**/АПИ/холографик/симулатион/рекординг/старт (POST)**

Начать запись. Одновременно может быть активна только одна запись. Необходимо задать один из головок, «руки», «Спатиалмаппинг» или «среда».

Параметры
* Head: задайте значение 1, чтобы записать данные заголовка.
* стрелки: значение 1, чтобы записать данные.
* Спатиалмаппинг: задайте значение 1 для записи пространственного сопоставления.
* окружение: задайте значение 1, чтобы записать данные среды.
* имя. имя записи.
* Синглеспатиалмаппингфраме: задайте значение 1, чтобы записать только один фрейм пространственного сопоставления.

**/АПИ/холографик/симулатион/рекординг/статус (GET)**

Получение состояния записи.

**/АПИ/холографик/симулатион/рекординг/стоп (GET)**

Останавливает текущую запись. Запись будет возвращена в виде файла.

## <a name="mixed-reality-capture"></a>Смешанный захват реальности

**/АПИ/холографик/МРК/филе (GET)**

Скачивает файл смешанной реальности с устройства. Use Op = потоковый параметр запроса для потоковой передачи.

Параметры
* имя файла: имя, hex64 в кодировке для получаемого видео.
* Op: Stream

**/АПИ/холографик/МРК/филе (удаление)**

Удаляет запись смешанной реальности с устройства.

Параметры
* filename: Name, hex64 Encoded (имя файла), которое нужно удалить.

**/АПИ/холографик/МРК/Филес (GET)**

Возвращает список файлов смешанной реальности, хранящихся на устройстве

**/АПИ/холографик/МРК/фото (POST)**

Принимает фотографию смешанной реальности и создает файл на устройстве

Параметры
* Холо: голограммы захвата: true или false (по умолчанию — false)
* ПС: захват ПС Camera: true или false (по умолчанию — false)
* Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)

**/АПИ/холографик/МРК/Сеттингс (GET)**

Получает параметры записи смешанной реальности по умолчанию

**/АПИ/холографик/МРК/Сеттингс (POST)**

Задает параметры записи смешанной реальности по умолчанию.  Некоторые из этих параметров применяются к фотографии и видеозаписи системы требований к системе.

**/АПИ/холографик/МРК/статус (GET)**

Возвращает состояние захвата смешанной реальности на портале устройств Windows.

***Ответ***

Ответ содержит свойство JSON, указывающее, записывается ли видео на портале устройств Windows.

``` javascript
{"IsRecording" : boolean}
```

**/АПИ/холографик/МРК/сумбнаил (GET)**

Получает эскиз изображения для указанного файла.

Параметры
* filename: Name, hex64 Encoded, файла, для которого запрашивается эскиз.

**/АПИ/холографик/МРК/видео/контрол/старт (POST)**

Запуск записи смешанной реальности

Параметры
* Холо: голограммы захвата: true или false (по умолчанию — false)
* ПС: захват ПС Camera: true или false (по умолчанию — false)
* MIC: записать микрофон: true или false (по умолчанию — false)
* замыкание на себя: запись звука приложения: true или false (по умолчанию — false)
* Рендерфромкамера: (только HoloLens 2) отрисовывается с точки зрения фотографии или видеокамеры: true или false (значение по умолчанию — true)
* встаб: (только HoloLens 2) Enable Video стабилизации: true или false (значение по умолчанию — true)
* встаббуффер: (только HoloLens 2) задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)

**/АПИ/холографик/МРК/видео/контрол/стоп (POST)**

Останавливает текущую запись смешанной реальности

## <a name="mixed-reality-streaming"></a>Потоковая передача смешанной реальности

HoloLens поддерживает динамическую предварительную версию смешанной реальности через частную загрузку фрагментированного MP4.

Потоки смешанной реальности используют один и тот же набор параметров для управления тем, что захватывается:
* Холо: голограммы записи: true или false
* ПС: запись камеры PV: true или false
* микрофон: записать микрофон: true или false
* замыкание на себя: запись звука приложения: true или false

Если ни один из этих элементов не указан: будут записываться голограммы, Фото-и видеокамера и звук приложения<br>
Если таковые имеются, то по умолчанию для неуказанных параметров будет задано значение false.

Необязательные параметры (только HoloLens 2)
* Рендерфромкамера: прорисовка с точки зрения фотографии или видеокамеры: true или false (по умолчанию — true)
* встаб: enable Video стабилизации: true или false (по умолчанию — false)
* встаббуффер: задержка буфера стабилизации видео: от 0 до 30 кадров (по умолчанию — 15 кадров)

**live.mp4/АПИ/холографик/стреам/(GET)**

1280x720p 30fps 5Mbit Stream.

**live_high.mp4/АПИ/холографик/стреам/(GET)**

1280x720p 30fps 5Mbit Stream.

**live_med.mp4/АПИ/холографик/стреам/(GET)**

Поток 854x480p 30fps 2.5 Мбит.

**live_low.mp4/АПИ/холографик/стреам/(GET)**

Поток 428x240p 15fps 0,6 Мбит.

## <a name="networking"></a>Сети

**/АПИ/нетворкинг/ипконфиг (GET)**

Возвращает текущую IP-конфигурацию

## <a name="os-information"></a>Сведения о ОС

**/АПИ/ОС/Инфо (GET)**

Получение сведений об операционной системе

**/АПИ/ОС/мачиненаме (GET)**

Возвращает имя компьютера.

**/АПИ/ОС/мачиненаме (POST)**

Задает имя компьютера

Параметры
* Имя: новое имя компьютера, hex64 в кодировке, для которого задано значение.

## <a name="performance-data"></a>Данные о производительности

**/АПИ/ресаурцеманажер/процессес (GET)**

Возвращает список запущенных процессов с подробными сведениями

Возвращать данные
* JSON со списком процессов и сведений для каждого процесса

**/АПИ/ресаурцеманажер/системперф (GET)**

Возвращает статистику производительности системы (операции чтения и записи ввода-вывода, статистика памяти и т. д.).

Возвращать данные
* JSON со сведениями о системе: ЦП, GPU, память, сеть, IO

## <a name="power"></a>Мощный

**/АПИ/повер/Баттери (GET)**

Возвращает текущее состояние аккумулятора

**/АПИ/повер/Стате (GET)**

Проверяет, находится ли система в состоянии с низким энергопотреблением

## <a name="remote-control"></a>Удаленное управление

**/АПИ/контрол/рестарт (POST)**

Перезапускает целевое устройство

**/АПИ/контрол/шутдовн (POST)**

Завершает работу целевого устройства

## <a name="task-manager"></a>Диспетчер задач

**/АПИ/таскманажер/АПП (удаление)**

Останавливает современное приложение

Параметры
* Package: полное имя пакета приложения, hex64 в кодировке
* форцестоп: принудительно останавливаются все процессы (= да)

**/АПИ/таскманажер/АПП (POST)**

Запуск современного приложения

Параметры
* AppID: ПРАИД приложения для запуска, hex64 в кодировке
* Package: полное имя пакета приложения, hex64 в кодировке

## <a name="wifi-management"></a>Управление Wi-Fi

**/АПИ/ВИФИ/интерфацес (GET)**

Перечисляет беспроводные сетевые интерфейсы

Возвращать данные
* Список беспроводных интерфейсов с подробными сведениями (GUID, описание и т. д.).

**/АПИ/ВИФИ/Нетворк (удаление)**

Удаление профиля, связанного с сетью, в указанном интерфейсе

Параметры
* интерфейс: GUID сетевого интерфейса
* Профиль: имя профиля

**/АПИ/ВИФИ/Нетворкс (GET)**

Перечисляет беспроводные сети в указанном сетевом интерфейсе

Параметры
* интерфейс: GUID сетевого интерфейса

Возвращать данные
* Список беспроводных сетей, обнаруженных в сетевом интерфейсе, с подробными сведениями

**/АПИ/ВИФИ/Нетворк (POST)**

Подключение к сети или отключение от него по указанному интерфейсу

Параметры
* интерфейс: GUID сетевого интерфейса
* SSID: SSID, hex64 в кодировке для подключения
* Операция: подключение или отключение
* креатепрофиле: Да или нет
* ключ: Shared Key, hex64 Encoded

## <a name="windows-performance-recorder"></a>Средство записи производительности Windows

**/АПИ/ВПР/кустомтраце (POST)**

Отправляет профиль ЗВЧ и начинает трассировку с помощью отправленного профиля.

Полезные данные
* текст HTTP из нескольких частей

Возвращать данные
* Возвращает состояние сеанса ЗВЧ.

**/АПИ/ВПР/статус (GET)**

Получение состояния сеанса ЗВЧ

Возвращать данные
* Состояние сеанса ЗВЧ.

**/АПИ/ВПР/траце (GET)**

Останавливает сеанс трассировки ЗВЧ (производительность)

Возвращать данные
* Возвращает ETL-файл трассировки

**/АПИ/ВПР/траце (POST)**

Запускает сеансы трассировки ЗВЧ (производительность)

Параметры
* Профиль: имя профиля. Доступные профили хранятся в перфпрофилес/profiles.jsна

Возвращать данные
* При запуске возвращает состояние сеанса ЗВЧ.

## <a name="see-also"></a>См. также
* [Использование портала устройств Windows](using-the-windows-device-portal.md)
* [Справочник по API для базовых порталов устройств (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
