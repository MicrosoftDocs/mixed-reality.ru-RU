---
title: Покупки из приложения
description: Покупки из приложений поддерживаются в приложениях смешанной реальности, но для их настройки требуется определенная работа.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: покупки в приложении, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515290"
---
# <a name="in-app-purchases"></a><span data-ttu-id="0de4d-104">Покупки из приложения</span><span class="sxs-lookup"><span data-stu-id="0de4d-104">In-app purchases</span></span>

<span data-ttu-id="0de4d-105">Покупки из приложений поддерживаются в HoloLens, но для их настройки требуется определенная работа.</span><span class="sxs-lookup"><span data-stu-id="0de4d-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="0de4d-106">Чтобы использовать функцию в функции приобретения приложений, необходимо:</span><span class="sxs-lookup"><span data-stu-id="0de4d-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="0de4d-107">Создание 2D- [представления](app-views.md) XAML для отображения в виде планшета</span><span class="sxs-lookup"><span data-stu-id="0de4d-107">Create a XAML [2D view](app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="0de4d-108">Переключитесь на него, чтобы активировать размещение, которое оставляет иммерсивное представление</span><span class="sxs-lookup"><span data-stu-id="0de4d-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="0de4d-109">Вызовите API: await [куррентапп. рекуестпродуктпурчасеасинк ("дураблеитемиапнаме");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span><span class="sxs-lookup"><span data-stu-id="0de4d-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="0de4d-110">Этот API отобразит всплывающее окно ОС Windows, в котором отображается название, описание и цена покупки в приложении.</span><span class="sxs-lookup"><span data-stu-id="0de4d-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="0de4d-111">Затем пользователь может выбрать вариант приобретения.</span><span class="sxs-lookup"><span data-stu-id="0de4d-111">The user can then choose purchase options.</span></span> <span data-ttu-id="0de4d-112">После завершения действия приложение должно предоставить пользовательский интерфейс, который позволяет пользователю вернуться в его [иммерсивное представление](app-views.md).</span><span class="sxs-lookup"><span data-stu-id="0de4d-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](app-views.md).</span></span>

<span data-ttu-id="0de4d-113">Для приложений, предназначенных для впечатляющих головных телефонов Windows Mixed Reality, не требуется вручную переключаться на представление XAML перед вызовом API Рекуестпродуктпурчасеасинк.</span><span class="sxs-lookup"><span data-stu-id="0de4d-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
