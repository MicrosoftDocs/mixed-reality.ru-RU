---
title: Общие сведения о базовом модуле MR Learning
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 3c779d731d7cf139ebcbe305c94754970e937b57
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293614"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="1172d-104">1. Общие сведения и цели</span><span class="sxs-lookup"><span data-stu-id="1172d-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="1172d-105">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="1172d-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1172d-106"><strong>Хождение</strong></span><span class="sxs-lookup"><span data-stu-id="1172d-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="1172d-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1172d-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1172d-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="1172d-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="1172d-109"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="1172d-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="1172d-110">❌</span><span class="sxs-lookup"><span data-stu-id="1172d-110">❌</span></span></td>
        <td><span data-ttu-id="1172d-111">✔️</span><span class="sxs-lookup"><span data-stu-id="1172d-111">✔️</span></span></td>
        <td><span data-ttu-id="1172d-112">❌</span><span class="sxs-lookup"><span data-stu-id="1172d-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1172d-113">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="1172d-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1172d-114">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="1172d-114">Prerequisites</span></span>

* <span data-ttu-id="1172d-115">КОМПЬЮТЕР с Windows 10 с установленными правильными [инструментами](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="1172d-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="1172d-116">Windows 10 SDK 10.0.18362.0 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="1172d-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="1172d-117">Некоторые базовые C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="1172d-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="1172d-118">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="1172d-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

[<span data-ttu-id="1172d-119">Следующий урок. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="1172d-119">Next Lesson: Initializing your project and first application</span></span>](mrlearning-base-ch1.md)