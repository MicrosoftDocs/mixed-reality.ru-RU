---
title: Взгляните на входные данные в нереальном режиме
description: Объясняется, как использовать ввод с помощью взгляда в нереальных
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, HoloLens, отслеживание глаз
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835631"
---
# <a name="gaze-input"></a>Входные данные взгляда

Подключаемый модуль Windows Mixed Reality не предоставляет никаких специальных функций для ввода с помощью взгляда. Все работает, несмотря на стандартный нереалй API.

[API головного взгляда](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a>Отслеживание взгляда

Чтобы использовать API отслеживания взгляда, разработчики должны включить возможность ввода с помощью взгляда в параметрах проекта HoloLens. При запуске приложения пользователь увидит следующее приглашение на согласие

![Разрешения на вход с глазами](images/unreal/eye-input-permissions.png)
 
Если пользователь предоставит свое разрешение, приложение получит доступ к входным данным. 

[Здесь](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html) приведена документация по API отслеживания взгляда на нереалию

Технические сведения об отслеживании глаз [here](eye-tracking.md)

Обратите внимание, что в частности, для отслеживания взгляда HoloLens в обоих глаза есть один луч. HoloLens не обеспечивает отслеживание стереоскопикных глаз.
