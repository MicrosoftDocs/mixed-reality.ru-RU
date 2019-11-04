---
title: Использование Вебвр в Microsoft погранично с Windows Mixed Reality
description: Общие сведения об использовании и разработке для Вебвр в Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: Вебвр, Вебкср, Винмр, Вебар, Web VR, Web XR, Web MR, Web AR, 360, 360 Video, 360 видео, 360 Photo, 360 Фото, 360 Content, иммерсивное веб-, иммерсивевеб, IW
ms.openlocfilehash: 87805d2c40e9e63cdf3e432189b9deb7d575a380
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437207"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="e4343-104">Использование Вебвр в Microsoft погранично с Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e4343-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="e4343-105">Создание содержимого Вебвр для впечатляющих головных телефонов Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e4343-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="e4343-106">Вебвр 1,1 доступна в Microsoft ребре, начиная с обновления Windows 10 для дизайнеров.</span><span class="sxs-lookup"><span data-stu-id="e4343-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="e4343-107">Теперь разработчики могут использовать этот API для создания впечатляющих функций VR в Интернете.</span><span class="sxs-lookup"><span data-stu-id="e4343-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="e4343-108">API Вебвр предоставляет на страницу данные ХМД, которые можно использовать для отображения стерео WebGL сцены обратно в ХМД.</span><span class="sxs-lookup"><span data-stu-id="e4343-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="e4343-109">Дополнительные сведения о поддержке API см. на [странице состояния платформы Microsoft ребра](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="e4343-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="e4343-110">Контактная зона API Вебвр доступна всегда в Microsoft ребро.</span><span class="sxs-lookup"><span data-stu-id="e4343-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="e4343-111">Однако вызов Жетврдисплайс () возвратит гарнитуру только в том случае, если телефонная гарнитура подключена или симулятор включен.</span><span class="sxs-lookup"><span data-stu-id="e4343-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="e4343-112">Просмотр содержимого Вебвр в впечатляющих головных гарнитурах Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e4343-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="e4343-113">Инструкции по доступу к содержимому Вебвр в иммерсивное гарнитуру можно найти в статье [о программе энтузиастов](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="e4343-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="e4343-114">См. также</span><span class="sxs-lookup"><span data-stu-id="e4343-114">See Also</span></span>
* [<span data-ttu-id="e4343-115">Сведения о Вебвр</span><span class="sxs-lookup"><span data-stu-id="e4343-115">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="e4343-116">Спецификация Вебвр</span><span class="sxs-lookup"><span data-stu-id="e4343-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="e4343-117">[API Вебвр](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="e4343-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="e4343-118">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="e4343-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="e4343-119">Расширения [API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) и [игровой](https://w3c.github.io/gamepad/extensions.html) планшета</span><span class="sxs-lookup"><span data-stu-id="e4343-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="e4343-120">Обработка потерянного контекста в WebGL</span><span class="sxs-lookup"><span data-stu-id="e4343-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="e4343-121">поинтерлокк</span><span class="sxs-lookup"><span data-stu-id="e4343-121">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="e4343-122">глтф</span><span class="sxs-lookup"><span data-stu-id="e4343-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="e4343-123">Использование Бабилон. js для включения Вебвр</span><span class="sxs-lookup"><span data-stu-id="e4343-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

