---
title: С помощью WebVR в Microsoft Edge с Windows Mixed Reality
description: Общие сведения о использовании и разработке для WebVR в Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, веб-vr, веб-xr, веб-mr, веб-ar, 360, 360 видео 360 видео, 360 фотографий, 360 фотографий, 360 содержимое, иммерсивных web, immersiveweb IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604636"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="8896f-104">С помощью WebVR в Microsoft Edge с Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8896f-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="8896f-105">Создание содержимого WebVR для Windows смешанной реальности иммерсивную</span><span class="sxs-lookup"><span data-stu-id="8896f-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="8896f-106">WebVR 1.1 доступен в Microsoft Edge, начиная с Windows 10 Fall Creators Update.</span><span class="sxs-lookup"><span data-stu-id="8896f-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="8896f-107">Разработчики теперь могут использовать этот API для создания мощных приложений виртуальной Реальности в Интернете.</span><span class="sxs-lookup"><span data-stu-id="8896f-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="8896f-108">WebVR API предоставляет данные поза HMD страницу, которая может использоваться для отображения сцены WebGL издавать HMD.</span><span class="sxs-lookup"><span data-stu-id="8896f-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="8896f-109">Сведения о поддержке API можно найти в [странице состояние платформы Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span><span class="sxs-lookup"><span data-stu-id="8896f-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="8896f-110">Контактная зона WebVR API присутствует на все время в Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="8896f-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="8896f-111">Тем не менее вызов getVRDisplays() вернет только гарнитуры Если подсоединено гарнитуры или симуляторе был включен.</span><span class="sxs-lookup"><span data-stu-id="8896f-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="8896f-112">Просмотр содержимого WebVR в Windows Mixed Reality иммерсивную</span><span class="sxs-lookup"><span data-stu-id="8896f-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="8896f-113">Инструкции для доступа к содержимому WebVR в вашей иммерсивных гарнитура можно найти в [кого руководство](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span><span class="sxs-lookup"><span data-stu-id="8896f-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="8896f-114">См. также</span><span class="sxs-lookup"><span data-stu-id="8896f-114">See Also</span></span>
* [<span data-ttu-id="8896f-115">Сведения о WebVR</span><span class="sxs-lookup"><span data-stu-id="8896f-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="8896f-116">Спецификация WebVR</span><span class="sxs-lookup"><span data-stu-id="8896f-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="8896f-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="8896f-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="8896f-118">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="8896f-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="8896f-119">[Игровой API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) и [расширения Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="8896f-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="8896f-120">Обработка потери контекста в WebGL</span><span class="sxs-lookup"><span data-stu-id="8896f-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="8896f-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="8896f-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="8896f-122">glTF</span><span class="sxs-lookup"><span data-stu-id="8896f-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="8896f-123">С помощью Babylon.js, чтобы включить WebVR</span><span class="sxs-lookup"><span data-stu-id="8896f-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

