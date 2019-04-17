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
# <a name="in-app-purchases"></a><span data-ttu-id="d9809-104">Покупки из приложения</span><span class="sxs-lookup"><span data-stu-id="d9809-104">In-app purchases</span></span>

<span data-ttu-id="d9809-105">Покупки из приложений поддерживаются в HoloLens, но настроить их выполнить ряд действий.</span><span class="sxs-lookup"><span data-stu-id="d9809-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="d9809-106">Чтобы использовать в приложении на покупку функциональные возможности, вы должны:</span><span class="sxs-lookup"><span data-stu-id="d9809-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="d9809-107">Создание XAML [двухмерном виде](app-views.md) отображались как баннер</span><span class="sxs-lookup"><span data-stu-id="d9809-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="d9809-108">Перейти к нему для активации размещения, который покидает область иммерсивных</span><span class="sxs-lookup"><span data-stu-id="d9809-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="d9809-109">Вызов API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="d9809-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="d9809-110">Этот API приведет к появлению акций всплывающее окно ОС Windows, отображается имя Покупка из приложения, описание и цена.</span><span class="sxs-lookup"><span data-stu-id="d9809-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="d9809-111">Затем пользователь может выбрать варианты приобретения.</span><span class="sxs-lookup"><span data-stu-id="d9809-111">The user can then choose purchase options.</span></span> <span data-ttu-id="d9809-112">После завершения действия, приложение должно предоставить пользовательский Интерфейс, позволяющий пользователю, чтобы вернуться к его [иммерсивных представление](app-views.md).</span><span class="sxs-lookup"><span data-stu-id="d9809-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="d9809-113">Для приложений, нацеленных на основе рабочего стола Windows Mixed Reality иммерсивную он не требуется для переключения в представление XAML перед вызовом RequestProductPurchaseAsync API.</span><span class="sxs-lookup"><span data-stu-id="d9809-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
