---
title: Покупки из приложения
description: Покупки из приложений, поддерживаются в приложениях смешанной реальности, но настроить их выполнить ряд действий.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: покупки из приложений, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602879"
---
# <a name="in-app-purchases"></a>Покупки из приложения

Покупки из приложений поддерживаются в HoloLens, но настроить их выполнить ряд действий.

Чтобы использовать в приложении на покупку функциональные возможности, вы должны:
* Создание XAML [двухмерном виде](app-views.md) отображались как баннер
* Перейти к нему для активации размещения, который покидает область иммерсивных
* Вызов API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Этот API приведет к появлению акций всплывающее окно ОС Windows, отображается имя Покупка из приложения, описание и цена. Затем пользователь может выбрать варианты приобретения. После завершения действия, приложение должно предоставить пользовательский Интерфейс, позволяющий пользователю, чтобы вернуться к его [иммерсивных представление](app-views.md).

Для приложений, нацеленных на основе рабочего стола Windows Mixed Reality иммерсивную он не требуется для переключения в представление XAML перед вызовом RequestProductPurchaseAsync API.
