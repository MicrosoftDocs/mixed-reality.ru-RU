---
title: Использование Вебкср с Windows Mixed Reality
description: Общие сведения об использовании и разработке для Вебкср в Windows Mixed Reality
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: Вебкср, Винмр, Вебар, Вебвр, Виндовсмикседреалити, HoloLens, Windows Mixed Reality, веб-VR, Web XR, Web MR, Web AR, 360, 360 Video, 360 видео, 360 Photo, 360 фотографии, 360 Content, иммерсивное веб-, иммерсивевеб, IW
ms.openlocfilehash: 01e6cd44e9879cd7fd9b11e178134eaf364cc53c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278445"
---
# <a name="webxr-overview"></a><span data-ttu-id="488bf-104">Обзор Вебкср</span><span class="sxs-lookup"><span data-stu-id="488bf-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="488bf-105">Что такое Вебкср</span><span class="sxs-lookup"><span data-stu-id="488bf-105">What is WebXR</span></span>

<span data-ttu-id="488bf-106">**API устройства вебкср** предназначен для доступа к устройствам **Virtual Reality (VR)** и **дополненным (AR)** , включая **датчики** и **подключенные к головным выдисплеям** в **Интернете**.</span><span class="sxs-lookup"><span data-stu-id="488bf-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="488bf-107">API устройства Вебкср в настоящее время доступен в Microsoft погранично, а версия Chrome 79 и более поздних версий поддерживает Вебкср по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="488bf-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="488bf-108">Последнюю версию поддержки браузера для Вебкср можно узнать по адресу [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="488bf-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="488bf-109">Узнайте больше о [Windows Mixed Reality и новом Microsoft ребре](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)в разделе [новые](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) возможности.</span><span class="sxs-lookup"><span data-stu-id="488bf-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="488bf-110">Просмотр Вебкср</span><span class="sxs-lookup"><span data-stu-id="488bf-110">Viewing WebXR</span></span>

<span data-ttu-id="488bf-111">Чтобы проверить, поддерживает ли ваш браузер Вебкср, перейдите к [примерам вебкср](https://immersive-web.github.io/webxr-samples/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="488bf-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="488bf-112">См. также</span><span class="sxs-lookup"><span data-stu-id="488bf-112">See Also</span></span>

* [<span data-ttu-id="488bf-113">Спецификация API устройства Вебкср</span><span class="sxs-lookup"><span data-stu-id="488bf-113">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="488bf-114">Документация по API устройства Вебкср</span><span class="sxs-lookup"><span data-stu-id="488bf-114">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="488bf-115">Иммерсивевеб. dev</span><span class="sxs-lookup"><span data-stu-id="488bf-115">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="488bf-116">Примеры Вебкср</span><span class="sxs-lookup"><span data-stu-id="488bf-116">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="488bf-117">Windows Mixed Reality и новая Microsoft ребро</span><span class="sxs-lookup"><span data-stu-id="488bf-117">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="488bf-118">Иммерсивное веб-сайт W3C GitHub</span><span class="sxs-lookup"><span data-stu-id="488bf-118">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="488bf-119">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="488bf-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="488bf-120">Расширения [API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) и [игровой](https://w3c.github.io/gamepad/extensions.html) планшета</span><span class="sxs-lookup"><span data-stu-id="488bf-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="488bf-121">Обработка потерянного контекста в WebGL</span><span class="sxs-lookup"><span data-stu-id="488bf-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="488bf-122">поинтерлокк</span><span class="sxs-lookup"><span data-stu-id="488bf-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="488bf-123">глтф</span><span class="sxs-lookup"><span data-stu-id="488bf-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="488bf-124">Использование Бабилон. js для создания Вебксрных возможностей</span><span class="sxs-lookup"><span data-stu-id="488bf-124">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="488bf-125">Группа иммерсивного веб-сообщества</span><span class="sxs-lookup"><span data-stu-id="488bf-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
