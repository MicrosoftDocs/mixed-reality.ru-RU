---
title: Взгляните на входные данные в нереальном режиме
description: Руководство по настройке входных данных взгляда для HoloLens и нереального модуля
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, голограммы, HoloLens 2, отслеживание глаз, входные данные с головного экрана, нереалная подсистема
ms.openlocfilehash: c77e33df2a1dfffdb5ea55e685d30af3fc2a22da
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330626"
---
# <a name="gaze-input"></a>Входные данные взгляда

## <a name="overview"></a>Обзор

[Подключаемый модуль Windows Mixed Reality](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) не предоставляет встроенных функций для ввода данных, но HoloLens 2 поддерживает отслеживание глаз. Фактические функции отслеживания предоставляются в виде интерфейсов API **монитора** и **отслеживания взгляда** в режиме реального времени и включают:

- Сведения об устройстве
- Датчики отслеживания
- Ориентация и положение
- Области обрезки
- Взгляните на данные и сведения об отслеживании

Полный список функций см. в документации по нереальному [подключению](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) и [отслеживания взглядов](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) . 

В дополнение к нереальным API-интерфейсам ознакомьтесь с документацией по [взаимодействию на основе взгляда](eye-gaze-interaction.md) для hololens 2 и прочитайте о работе [отслеживания взгляда в hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .

> [!IMPORTANT]
> Отслеживание взгляда поддерживается только в HoloLens 2. 

## <a name="enabling-eye-tracking"></a>Включение отслеживания взгляда
Необходимо включить входные данные для параметров проекта HoloLens, прежде чем можно будет использовать интерфейсы API нереального времени. При запуске приложения появится запрос на согласие, показанный на снимке экрана ниже.

- Выберите **Да** , чтобы задать разрешение и получить доступ к вводу с помощью взгляда. Если необходимо изменить этот параметр в любое время, его можно найти в приложении " **Параметры** ".

![Разрешения на вход с глазами](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> Отслеживание глаз HoloLens в нереальном режиме имеет один луч для обоих глаз, а не два луча, необходимых для отслеживания стереоскопик, что не поддерживается.

Это все, что необходимо для того, чтобы добавить входные данные взгляда в приложения HoloLens 2 в нереальном виде. Дополнительные сведения о вводе и том, как он влияет на пользователей в смешанной реальности, можно найти по ссылкам ниже. Не забудьте подумать об этих возможностях при создании интерактивных интерфейсов. 

## <a name="see-also"></a>См. также раздел
* [Калибровка](calibration.md)
* [Комфорт](comfort.md)
* [Взгляд и фиксация](gaze-and-commit.md)
* [Голосовой ввод](voice-design.md)