---
title: Рекомендации по производительности для Unreal
description: Рекомендации по оптимизации производительности для приложений смешанной реальности в Unreal
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, производительность, оптимизация, параметры, документация
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840203"
---
# <a name="performance-recommendations-for-unreal"></a>Рекомендации по производительности для Unreal

Эта статья является продолжением обсуждения, начатого в [рекомендациях по производительности для смешанной реальности](understanding-performance-for-mixed-reality.md), но посвящена более узким вопросам, имеющим отношение к среде Unreal Engine.

## <a name="recommended-unreal-project-settings"></a>Рекомендуемые параметры для проекта Unreal

- Используйте модуль отрисовки виртуальной реальности для мобильных устройств. В параметрах проекта обязательно установите значение целевой платформы Mobile/Tablet (Мобильное устройство или планшет) в разделе Project – Target Hardware (Проект — Целевое оборудование).
- Отключите отбрасывание загораживаемых объектов. На странице Engine (Система) — Rendering (Отрисовка) в разделе Culling (Отбрасывание) снимите флажок Occlusion Culling (Отбрасывание загораживаемых объектов).
    + Если отбрасывание загораживаемых объектов в вашем проекте необходимо для отрисовки очень подробной сцены, мы рекомендуем включить параметр Support Software Occlusion Culling (Поддержка программного отбрасывания загораживаемых объектов) в разделе Engine — Rendering (Система — Отрисовка). Это позволит Unreal выполнять отбрасывание загораживаемых объектов средствами ЦП, избегая запросов на отбрасывание к GPU, которые очень плохо работают на устройствах HoloLens 2.
- Включите параметры Instanced Stereo (Экземпляры стерео) и Mobile Multi-View (Просмотр на нескольких мобильных устройствах) в разделе Engine — Rendering (Система — Отрисовка) в категории VR (Виртуальная реальность). Возможно, для включения параметра Mobile Multi-View (Просмотр на нескольких мобильных устройствах) потребуется снять флажок Mobile Post-Processing (Постобработка на мобильном устройстве).