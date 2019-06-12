---
title: Введение базового обучения MR модуля
description: Выполните этот курс, чтобы узнать, как реализовать распознавание лиц Azure в приложениях смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Смешанная реальность, unity, руководство, hololens
ms.openlocfilehash: 2fe07efe87086e9a8c06e1953fcef8544b03c80a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829885"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="bb0c0-104">Общие сведения о модуле Base обучения MR & цели</span><span class="sxs-lookup"><span data-stu-id="bb0c0-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="bb0c0-105">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="bb0c0-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bb0c0-106"><strong>Курс</strong></span><span class="sxs-lookup"><span data-stu-id="bb0c0-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="bb0c0-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="bb0c0-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="bb0c0-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="bb0c0-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="bb0c0-109"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="bb0c0-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="bb0c0-110">❌</span><span class="sxs-lookup"><span data-stu-id="bb0c0-110">❌</span></span></td>
        <td><span data-ttu-id="bb0c0-111">✔️</span><span class="sxs-lookup"><span data-stu-id="bb0c0-111">✔️</span></span></td>
        <td><span data-ttu-id="bb0c0-112">❌</span><span class="sxs-lookup"><span data-stu-id="bb0c0-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="bb0c0-113">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="bb0c0-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="bb0c0-114">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="bb0c0-114">Prerequisites</span></span>

* <span data-ttu-id="bb0c0-115">ПК Windows 10, настроены с правильным [установлены инструменты](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="bb0c0-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="bb0c0-116">Пакет SDK для Windows 10 10.0.18362.0 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="bb0c0-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="bb0c0-117">Основные C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="bb0c0-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="bb0c0-118">Устройство HoloLens 2 [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="bb0c0-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
