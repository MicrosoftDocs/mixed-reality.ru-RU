---
title: Устранение неполадок Опенкср
description: Устранение неполадок в приложениях Опенкср.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Опенкср, Кхронос, Басикксрапп, DirectX, Native, собственное приложение, настраиваемое ядро, по промежуточного слоя, устранение неполадок
ms.openlocfilehash: 269982596ed6162d9c2f1ec999a446bcecd6ba2a
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228009"
---
# <a name="openxr-troubleshooting"></a>Устранение неполадок Опенкср

Ниже приведены некоторые советы по устранению неполадок при разработке приложения Опенкср с использованием среды выполнения Опенкср Windows Mixed Reality.  Если у вас есть другие вопросы о <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">спецификации опенкср 1,0</a>, посетите <a href="https://community.khronos.org/c/openxr" target="_blank">форумы Кхронос опенкср</a> или <a href="https://khr.io/slack" target="_blank">резервный #openxr канал</a>.

>[!NOTE]
>Существуют известные проблемы в текущей среде выполнения Windows Mixed Reality Опенкср с приложениями x86.  В данный момент следует создать классические приложения Опенкср для x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Приложение Опенкср не запускает Windows Mixed Reality

Если приложение Опенкср не запускает Windows Mixed Reality при запуске, то среда выполнения Windows Mixed Reality Опенкср может быть не установлена в качестве активной среды выполнения.  Следуйте приведенным выше инструкциям по [началу работы с опенкср для головных телефонов Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) , чтобы активировать среду выполнения.

Вы также можете запустить [средства для разработчиков Опенкср Windows Mixed Reality](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) для получения дополнительных сведений об устранении неполадок, связанных с состоянием среды выполнения Windows Mixed Reality опенкср в системе.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>На портале Mixed Reality не отображается пункт меню "Настройка Опенкср"

Убедитесь, что вы используете по крайней мере обновление Windows 10 октября 2018 (1809).  Если вы используете более раннюю версию Windows 10, можно выполнить обновление до 2019 обновления (1903) с помощью [помощника по обновлению Windows 10](https://www.microsoft.com//software-download/windows10).

Пункт меню "настроить Опенкср" может быть недоступен, если у вас более старая версия приложения портала смешанной реальности.  Проверьте наличие [обновления для приложения портала смешанной реальности](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) , чтобы убедиться, что у вас установлена последняя версия.

Обратите внимание, что пункт меню "настроить Опенкср" не отображается, если среда выполнения Windows Mixed Reality Опенкср уже установлена и активна.  Вы можете установить [средства для разработчиков Windows Mixed Reality опенкср](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) , чтобы определить текущее состояние среды выполнения опенкср в системе.