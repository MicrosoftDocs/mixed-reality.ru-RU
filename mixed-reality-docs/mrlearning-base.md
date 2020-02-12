---
title: Учебники по началу работы — 1. Общие сведения и цели
description: В этом курсе показано, как реализовать распознавание лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: dbae7545edb6515b5cf148fbbfb6652595d2fc0d
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129265"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="1c432-105">1. Общие сведения и цели</span><span class="sxs-lookup"><span data-stu-id="1c432-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="1c432-106">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="1c432-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1c432-107"><strong>Хождение</strong></span><span class="sxs-lookup"><span data-stu-id="1c432-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="1c432-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1c432-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1c432-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="1c432-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="1c432-110"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="1c432-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="1c432-111">✔️</span><span class="sxs-lookup"><span data-stu-id="1c432-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1c432-112">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="1c432-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1c432-113">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="1c432-113">Prerequisites</span></span>

* <span data-ttu-id="1c432-114">КОМПЬЮТЕР с Windows 10 с [установленными](install-the-tools.md) правильными инструментами</span><span class="sxs-lookup"><span data-stu-id="1c432-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="1c432-115">Windows 10 SDK 10.0.18362.0 или более поздней версии</span><span class="sxs-lookup"><span data-stu-id="1c432-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="1c432-116">Некоторые базовые C# возможности программирования</span><span class="sxs-lookup"><span data-stu-id="1c432-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="1c432-117">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="1c432-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="1c432-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Центр Unity</a> с установленным Unity 2019.2. X и добавлен модуль поддержки универсальная платформа Windows сборки</span><span class="sxs-lookup"><span data-stu-id="1c432-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c432-119">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2. X.</span><span class="sxs-lookup"><span data-stu-id="1c432-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="1c432-120">Это заменяет все требования к версии Unity или рекомендации, указанные в связанных выше условиях.</span><span class="sxs-lookup"><span data-stu-id="1c432-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="1c432-121">Следующее занятие: 2. Инициализация проекта и первого приложения</span><span class="sxs-lookup"><span data-stu-id="1c432-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
