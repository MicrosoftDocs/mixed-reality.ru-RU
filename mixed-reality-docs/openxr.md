---
title: OpenXR
description: Попробуйте API OpenXR 0.90, временное со смешанной реальности OpenXR Developer Preview.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Смешанная реальность OpenXR Developer Preview
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603663"
---
# <a name="openxr"></a>OpenXR

OpenXR является открытым стандартом отчислений от [Khronos](https://www.khronos.org/) , предоставляет собственный доступ к широким спектром устройств из многих поставщиков, которые охватывают [спектра смешанной реальности](mixed-reality.md).

С помощью OpenXR, вы можете создавать приложения, предназначенные как holographic устройствами (например, HoloLens 2), поместите цифрового содержимого в реальном мире, как если бы он был действительно существует, так и иммерсивных устройствами (например, гарнитуры смешанной реальности Windows для настольных ПК), которые скрывают физического мира и замените его цифрового маркетинга.  OpenXR позволяет писать код, если, можно затем переносить в самых различных аппаратных платформ.

Стандартный OpenXR находится в настоящее время на временное этапе с начальной спецификациями OpenXR 0.90, выпущенное для обратной связи.  Дополнительные сведения о OpenXR, включая доступ к [временное 0.90 спецификации](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) и [заголовки](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), см. в разделе [Khronos OpenXR страницы](https://www.khronos.org/openxr/).

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a>Настройка смешанной реальности OpenXR Developer Preview

Попробуйте API, вы можете OpenXR 0.90, сегодняшний день при использовании смешанной реальности OpenXR Developer Preview.  Этот ранний среда выполнения позволяет приложения, предназначенные для API OpenXR 0.90, чтобы Windows Mixed Reality иммерсивную целевой на рабочем столе.  Если у вас нет доступа к гарнитуры, смешанной реальности симулятор Windows можно использовать вместо этого.

Чтобы приступить к работе со смешанной реальности OpenXR Developer Preview:

1. Убедитесь, что выполняется по крайней мере Windows обновление 10 октября 2018 г.  Если вы используете более раннюю версию Windows 10, можно обновить до октября 2018 обновление с помощью [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).  Если у вас рискнуть, вы можете установить [сборки Windows 10 Insider Preview](https://insider.windows.com).
1. Установка гарнитуры смешанной реальности Windows или следуйте инструкциям, чтобы [включить в симуляторе Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md).
1. Установка [смешанной реальности OpenXR для разработчиков приложений](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Получает это приложение можно настроить с помощью предварительной версии среды выполнения OpenXR в Windows 10 октября 2018 г. обновление или более поздней версии.  После установки этого приложения Windows Store будет обновлять среды выполнения.
1. Запустите приложение смешанной реальности OpenXR Developer Preview из меню "Пуск" и следуйте инструкциям, чтобы сделать активной среды выполнения.  В ближайшее время это приложение позволит вам изучить отладки других OpenXR.

![Смешанная реальность OpenXR для разработчиков приложений](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a>Поддержка Windows 10 октября 2018 с обновлением

Чтобы приступить к работе со смешанной реальности OpenXR Developer Preview на Windows 10 октября 2018 года обновления (текущая версия Windows), вам потребуется выполнить несколько дополнительных действий:

1. Выполните действия, чтобы установить смешанной реальности OpenXR Developer Preview.
1. Для смешанной реальности OpenXR Developer Preview в качестве системы, активной среды выполнения OpenXR, установить [смешанной реальности OpenXR разработчика совместимости пакет для предварительной версии](https://aka.ms/openxr-compat).

## <a name="building-a-test-openxr-app"></a>Создание тестового приложения OpenXR

[Hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR тестовое приложение показывает, как использовать различные части API.  Следуя этим [инструкции по построению](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md), который создаст тестовое приложение и сами заголовки OpenXR.

## <a name="feedback"></a>Отзыв

Чтобы оставить отзыв о [спецификации оговоренные предварительно OpenXR 0.90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), посетите [форумы OpenXR Khronos](https://community.khronos.org/c/openxr), [канал Slack #openxr](https://khr.io/slack) и [спецификации программа Issue tracker](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Устранение неполадок

Ниже приведены некоторые советы по устранению неполадок для смешанной реальности OpenXR Developer Preview.  Если вы встретились других проблем, посетите [форумы OpenXR Khronos](https://community.khronos.org/c/openxr) или [канал Slack #openxr](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR приложение не запускается Windows Mixed Reality

Если при запуске приложения OpenXR смешанной реальности Windows не запускается, смешанной реальности OpenXR Developer Preview не может задаваться как активную среду выполнения.  Не забудьте запустить приложение смешанной реальности OpenXR Developer Preview и следуйте инструкциям, чтобы сделать активной среды выполнения.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Невозможно установить приложение смешанной реальности OpenXR Developer Preview 

Убедитесь, что выполняется по крайней мере Windows обновление 10 октября 2018 г.  Если вы используете более раннюю версию Windows 10, можно обновить до октября 2018 обновление с помощью [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).

Если установку, нажмите кнопку приложения смешанной реальности OpenXR Developer Preview не ничего в Windows 10 октября 2018 г. обновления по, системы имеют кэшированных устаревшие системные требования для приложения.  Можно выполнить команду `wsreset.exe` из командной строки, чтобы очистить кэш.

## <a name="see-also"></a>См. также

* [Дополнительные сведения о OpenXR](https://www.khronos.org/openxr/)
* [Спецификация оговоренные предварительно OpenXR 0.90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Справочник по API оговоренные предварительно OpenXR 0.90](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [Заголовки оговоренные предварительно OpenXR 0.90](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
