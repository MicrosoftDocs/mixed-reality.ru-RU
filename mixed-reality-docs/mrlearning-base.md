---
title: Общие сведения о модуле MR обучения базы
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: d4220527a7de8e596f2825fd9d199d536510b972
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148628"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="27b97-104">Общие сведения о модуле Base обучения MR & цели</span><span class="sxs-lookup"><span data-stu-id="27b97-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="27b97-105">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="27b97-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="27b97-106"><strong>Курс</strong></span><span class="sxs-lookup"><span data-stu-id="27b97-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="27b97-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="27b97-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="27b97-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="27b97-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="27b97-109"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="27b97-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="27b97-110">❌</span><span class="sxs-lookup"><span data-stu-id="27b97-110">❌</span></span></td>
        <td><span data-ttu-id="27b97-111">✔️</span><span class="sxs-lookup"><span data-stu-id="27b97-111">✔️</span></span></td>
        <td><span data-ttu-id="27b97-112">❌</span><span class="sxs-lookup"><span data-stu-id="27b97-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="27b97-113">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="27b97-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="27b97-114">предварительные требования</span><span class="sxs-lookup"><span data-stu-id="27b97-114">Prerequisites</span></span>

* <span data-ttu-id="27b97-115">ПК Windows 10, настроены с правильным [установлены инструменты](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="27b97-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="27b97-116">Пакет SDK для Windows 10 10.0.18362.0 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="27b97-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="27b97-117">Основные C# возможности программирования.</span><span class="sxs-lookup"><span data-stu-id="27b97-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="27b97-118">Устройство HoloLens 2 [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="27b97-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
