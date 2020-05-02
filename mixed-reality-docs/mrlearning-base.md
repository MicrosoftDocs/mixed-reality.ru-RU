---
title: Серия руководств по началу работы, часть 1 Общие сведения и цели
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36c12d82759b8ac2ba24aa9af37a096e0faf5fb5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "80082051"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="23bee-105">1. Общие сведения и цели</span><span class="sxs-lookup"><span data-stu-id="23bee-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="23bee-106">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="23bee-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="23bee-107"><strong>Курс</strong></span><span class="sxs-lookup"><span data-stu-id="23bee-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="23bee-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="23bee-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="23bee-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="23bee-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="23bee-110"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="23bee-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="23bee-111">✔️</span><span class="sxs-lookup"><span data-stu-id="23bee-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="23bee-112">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="23bee-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="23bee-113">Предварительные условия</span><span class="sxs-lookup"><span data-stu-id="23bee-113">Prerequisites</span></span>

* <span data-ttu-id="23bee-114">Компьютер с Windows 10, настроенный с требуемыми [установленными инструментами](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="23bee-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="23bee-115">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="23bee-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="23bee-116">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="23bee-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="23bee-117">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="23bee-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="23bee-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> с Unity 2019.2.X и модулем поддержки сборки универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="23bee-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23bee-119">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="23bee-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="23bee-120">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="23bee-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="23bee-121">Следующий урок. 2. Инициализация проекта и первое приложение</span><span class="sxs-lookup"><span data-stu-id="23bee-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
