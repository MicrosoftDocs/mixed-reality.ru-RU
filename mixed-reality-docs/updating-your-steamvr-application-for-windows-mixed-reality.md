---
title: Обновление приложения Стеамвр
description: Рекомендации по обновлению приложения Стеамвр для оптимизации совместимости с помощью головных телефонов Windows Mixed Reality.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Стеамвр, совместимость
ms.openlocfilehash: 6479130b14b8b50828ebecd3a648fd8a425aec15
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438204"
---
# <a name="updating-your-steamvr-application"></a>Обновление приложения Стеамвр
Мы советуем разработчикам тестировать и оптимизировать свои Стеамврные возможности для работы на гарнитурах Windows Mixed Reality. В этой документации рассматриваются распространенные улучшения, которые могут быть реализованы разработчиками, чтобы гарантировать, что их работа отлично работает в Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Инструкции по начальной настройке

Чтобы начать тестирование игры или приложения в Windows Mixed Reality, обязательно ознакомьтесь с нашим [руководством по началу работы.](https://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Модели контроллеров
1. Если приложение подготавливает модели контроллеров:
    * Использование [моделей контроллеров движения Windows Mixed Reality](motion-controllers.md#rendering-the-motion-controller-model)
    * Используйте Ивррендермодел:: Жеткомпонентстате для получения локальных преобразований в части компонентов (например, Указатель a)
2. Опыт, имеющий понятие правой или левой, должен получать подсказки от входных API-интерфейсов для различения контроллеров [(пример Unity)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) .

## <a name="controls"></a>Элементы управления

При проектировании или настройке макета элемента управления учитывайте следующий набор зарезервированных команд:
1. Щелчок **левого и правого аналогового стика** зарезервировано для **панели мониторинга Steam**.
2. При **нажатии кнопки Windows** всегда будут возвращаться пользователи на домашнюю страницу Windows Mixed Reality.

Если это возможно, по умолчанию закрепить Телепорт на основе закрепления в соответствии с поведением [домашнего транспорта Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) .

## <a name="tooltips-and-ui"></a>Подсказки и пользовательский интерфейс

Многие игры VR используют преимущества всплывающих подсказок и наложения контроллера движения для обучения пользователям наиболее важных команд для их игры или приложения. При настройке приложения для Windows Mixed Reality рекомендуется проверить эту часть работы, чтобы убедиться, что всплывающие подсказки сопоставлены с моделями контроллера Windows.

Кроме того, при наличии каких бы то ни было точек в вашем интерфейсе, в которых отображаются образы контроллеров, вы должны предоставить обновленные образы с помощью контроллеров движения Windows Mixed Reality.

## <a name="haptics"></a>хаптикс

Начиная с [обновления Windows 10 от апреля 2018](release-notes-april-2018.md)г., хаптикс теперь поддерживаются для стеамврных возможностей Windows Mixed Reality. Если ваше приложение или игра Стеамвр уже включает поддержку хаптикс, теперь она должна работать (без дополнительной работы) с [контроллерами движения Windows Mixed Reality](motion-controllers.md).

Контроллеры движения Windows Mixed Reality используют стандартный мотор хаптикс, в отличие от линейных исполнителей, находящихся в некоторых других Стеамвр контроллерах движения, что может привести к слегка отличающимся впечатлениям от ожидаемого взаимодействия с пользователем. Поэтому мы рекомендуем тестировать и настраивать дизайн хаптикс с помощью контроллеров движения Windows Mixed Reality. Например, иногда короткие хаптик пульса (5-10 мс) менее заметны на контроллерах движения Windows Mixed Reality. Чтобы получить более заметный импульс, поэкспериментируйте с отправкой более длительного "щелчка" (40-70ms), чтобы придать мотору больше времени, прежде чем отключать питание.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Запуск приложений Стеамвр из меню "Пуск" Windows Mixed Reality

Для функций VR, распространяемых через Steam, мы [обновили бета-версию Windows Mixed Reality для Стеамвр Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) вместе с последними рейсами [Windows Insider](https://insider.windows.com) RS5, чтобы теперь заголовки стеамвр отображались в меню Пуск Windows Mixed Reality в «все приложения». список автоматически. После установки этих версий программного обеспечения клиенты смогут запускать заголовки Стеамвр непосредственно из дома Windows Mixed Reality, не удаляя их гарнитуры.

## <a name="windows-mixed-reality-logo"></a>Логотип Windows Mixed Reality

Чтобы отобразить поддержку Windows Mixed Reality для вашего заголовка, перейдите на ссылку "Изменить страницу хранилища" на целевой странице приложения, щелкните вкладку "Основные сведения" и прокрутите вниз до пункта "Виртуальная реальность". Снимите флажок "скрыть Windows Mixed Reality", а затем опубликуйте его в хранилище.

## <a name="bugs-and-feedback"></a>Ошибки и отзывы

Ваш отзыв не будет ценным, когда дело доходит до улучшения возможностей Стеамвр Windows Mixed Reality. Отправьте все отзывы и ошибки через [центр обратной связи Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Ниже приведены некоторые [советы о том, как сделать отзыв стеамвр как можно более удобным](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Если у вас есть вопросы или комментарии для совместного использования, вы также можете связаться с нами на нашем [форуме Steam](https://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Часто задаваемые вопросы и устранение неполадок

Если у вас возникли общие проблемы с настройкой или воспроизведением опыта, [Ознакомьтесь с последними действиями по устранению неполадок](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>См. также
* [Установка средств](install-the-tools.md)
* [Журнал драйверов контроллера гарнитуры и движения](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Минимальные рекомендации по совместимости Windows Mixed Reality с оборудованием ПК](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
