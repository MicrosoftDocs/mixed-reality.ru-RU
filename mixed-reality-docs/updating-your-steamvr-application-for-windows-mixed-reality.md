---
title: Обновление приложения для Windows Mixed Reality SteamVR
description: Рекомендации для обновления приложения SteamVR для обеспечения максимальной совместимости с гарнитуры смешанной реальности Windows.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR совместимости
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597856"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>Обновление приложения для Windows Mixed Reality SteamVR

Мы рекомендуем разработчикам тестировать и оптимизировать их опыт SteamVR гарнитуры смешанной реальности Windows под управлением. Общих улучшений, которые разработчики могут сделать, чтобы убедиться, что их работы отлично работает со смешанной реальностью Windows входит в эту документацию.

## <a name="initial-setup-instructions"></a>Инструкции по начальной настройке

Для запуска тестирования игры или приложения в Windows Mixed Reality убедитесь что на первый выполните наши [руководство по началу работы.](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Контроллер моделей
1. Если приложение отображает моделей контроллера:
    * Используйте [Windows Mixed Reality движения контроллера моделей](motion-controllers.md#rendering-the-motion-controller-model)
    * Используйте IVRRenderModel::GetComponentState для получения локального преобразует компонентов (например) Указатель поза)
2. Действия, которые необходимо иметь представление о рабочей руки пользователя должны получить указания входных данных в API-интерфейсы для различения контроллеров [(например, Unity)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Элементы управления

При создании или настройке макета элемента управления не забывайте следующий набор зарезервированных команд:
1. Щелкнув вниз **левой и правой аналоговых джойстик** зарезервирован для **пара мониторинга**.
2. **Кнопку Windows** всегда будет возвращать пользователей в Windows Mixed Reality home.

Если это возможно, по умолчанию, чтобы бегунок палочка основе teleportation в соответствии с [Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation поведение

## <a name="tooltips-and-ui"></a>Всплывающие подсказки и пользовательского интерфейса

Многие игры VR преимущества подсказки контроллера движения и наложения, чтобы обучить пользователей наиболее важные команды для их игры или приложения. При настройке приложения для Windows смешанной реальности рекомендуется рецензирование этой части работы, чтобы убедиться, что всплывающие подсказки, которые сопоставляются модели контроллера Windows.

Кроме того при наличии все точки в процесс, где отображение контроллеров не забудьте предоставить обновленные образы с помощью контроллеров движения смешанной реальности Windows.

## <a name="haptics"></a>Haptics

Начиная с версии [обновления Windows 10 апреля 2018 г.](release-notes-april-2018.md), haptics теперь поддерживаются для работы в SteamVR со смешанной реальностью Windows. Если SteamVR приложение или игра уже включает поддержку haptics, он должен работать теперь (с помощью дополнительных действий) с [контроллеров движения Windows Mixed Reality](motion-controllers.md).

Контроллеры движения Windows Mixed Reality использовать стандартный haptics двигатель, в отличие от линейной Приводные механизмы, в некоторых других SteamVR движения контроллеров, что может привести к немного разных ожидаемого при использовании. Таким образом мы рекомендуем, тестирования и настройки макета haptics с контроллерами Windows Mixed Reality движения. Например иногда коротких haptic импульсов (5 – 10 мс) менее заметны на контроллерах Windows Mixed Reality движения. Для создания более заметным pulse, поэкспериментируйте с отправкой больше «click» (40-70 мс) для предоставления motor больше времени для настройки еще не были получены для power off еще раз.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Запуск приложений SteamVR из меню Windows Пуск смешанной реальности

Для работы виртуальной Реальности, распространяемые через поток данных, мы улучшили [обновлены смешанной реальности Windows для бета-версии SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) вместе с последней [Windows Insider](https://insider.windows.com) рейсы RS5 таким образом, чтобы заголовки SteamVR теперь отображаются в Windows смешанной реальности меню "Пуск" в «все приложения» список автоматически. С помощью этих версий программного обеспечения заказчикам теперь можно запускать SteamVR издательства непосредственно в Windows Mixed Reality домашней, не удаляя их гарнитуры.

## <a name="windows-mixed-reality-logo"></a>Логотип Windows Mixed Reality

Для отображения Windows Mixed Reality поддержка название, перейдите по ссылке «Изменить страницу Store» на целевой странице приложения, перейдите на вкладку «Основные сведения» и прокрутите вниз до «Виртуальной реальности». Снимите флажок «Скрывать Windows Mixed Reality», а затем опубликовать в хранилище.

## <a name="bugs-and-feedback"></a>Ошибках и отзывы

Ваши отзывы очень полезным, когда дело доходит до повышения удобства работы смешанной реальности SteamVR Windows. Отправьте все отзывы и ошибок с помощью [центр обратной связи Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Ниже приведены некоторые [советы о том, как опубликовать ваше мнение о SteamVR, как информативное максимально](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Если у вас есть вопросы или комментарии для совместного использования, также нами можно связаться на наших [форум пара](http://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Часто задаваемые вопросы и устранение неполадок

Если у вас в общие вопросы по настройке или воспроизводится собственном опыте, [последних Узнайте](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>См. также
* [Установка средств](install-the-tools.md)
* [Журнал драйвера контроллера гарнитуры и перемещения](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality минимальное ПК совместимости рекомендаций по оборудованию](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
