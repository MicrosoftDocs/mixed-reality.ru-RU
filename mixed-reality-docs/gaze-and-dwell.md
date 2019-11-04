---
title: Взгляните и вдаваясь
description: Общие сведения о модели входных данных (глаз/Head) и вдаваясь
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Смешанная реальность, взгляд, вдаваясь, взаимодействие, проектирование, отслеживание глаз, отслеживание головок
ms.openlocfilehash: d87406d0b2695cd86c40f27cb132af54ed525b25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435353"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="a5b65-104">Взгляните и вдаваясь</span><span class="sxs-lookup"><span data-stu-id="a5b65-104">Gaze and dwell</span></span>

<span data-ttu-id="a5b65-105">Когда руки заняты инструментами и деталями, жестикулировать может быть сложно или невозможно.</span><span class="sxs-lookup"><span data-stu-id="a5b65-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="a5b65-106">Команды Voice также могут быть ненадежны в определенных контекстах, например в условиях чрезмерно громкой ситуации.</span><span class="sxs-lookup"><span data-stu-id="a5b65-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="a5b65-107">Взгляните и вдаваясь предлагает знакомый и простой механизм для работы с заголовком и практически без участия в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a5b65-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="a5b65-108">Кроме того, взгляните и вдаваясь — это отличная резервная версия, которая не зависит от помех шума или ограничений тишины в операционной среде.</span><span class="sxs-lookup"><span data-stu-id="a5b65-108">Additionally, gaze and dwell is a great fallback which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="a5b65-109">Мы определяем два варианта _взгляда и вдаваясь_: [head-взгляд и вдаваясь](gaze-and-dwell-head.md) , [глаза-взгляд и вдаваясь](gaze-and-dwell-eyes.md).</span><span class="sxs-lookup"><span data-stu-id="a5b65-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="a5b65-110">Сценарии</span><span class="sxs-lookup"><span data-stu-id="a5b65-110">Scenarios</span></span>

<span data-ttu-id="a5b65-111">Взгляните и вдаваясь предназначен в сценариях, где руки человека заняты другими задачами, а речь не 100% надежна или недоступна из-за ограничений среды или социальных сетей.</span><span class="sxs-lookup"><span data-stu-id="a5b65-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="a5b65-112">Хорошим примером является пользователь, носящий HoloLens для получения справочной информации при ремонте двигателя автомобиля.</span><span class="sxs-lookup"><span data-stu-id="a5b65-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="a5b65-113">Их руки заняты инструментами или поддержкой своего тела, когда они нагибаются в моторный отсек.</span><span class="sxs-lookup"><span data-stu-id="a5b65-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="a5b65-114">Гараж — шумный, с постоянным грохотом и гудением инструментов, что создает помехи голосовым командам.</span><span class="sxs-lookup"><span data-stu-id="a5b65-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="a5b65-115">Взгляните и вдаваясь позволяет пользователю, использующему HoloLens, уверенно перемещаться по справочным материалам, не прерывая рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="a5b65-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="a5b65-116">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="a5b65-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a5b65-117"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="a5b65-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="a5b65-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a5b65-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a5b65-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a5b65-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a5b65-120"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="a5b65-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a5b65-121">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="a5b65-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="a5b65-122">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="a5b65-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a5b65-123">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="a5b65-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a5b65-124">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="a5b65-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a5b65-125">Взгляд — взгляните и вдаваясь</span><span class="sxs-lookup"><span data-stu-id="a5b65-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="a5b65-126">❌ недоступна</span><span class="sxs-lookup"><span data-stu-id="a5b65-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="a5b65-127">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="a5b65-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a5b65-128">❌ недоступна</span><span class="sxs-lookup"><span data-stu-id="a5b65-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="a5b65-129">См. также</span><span class="sxs-lookup"><span data-stu-id="a5b65-129">See also</span></span>
* [<span data-ttu-id="a5b65-130">Взаимодействие на основе глаз</span><span class="sxs-lookup"><span data-stu-id="a5b65-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="a5b65-131">Отслеживание глаз в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a5b65-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="a5b65-132">Взгляните и зафиксируйте</span><span class="sxs-lookup"><span data-stu-id="a5b65-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a5b65-133">Руки — прямое управление</span><span class="sxs-lookup"><span data-stu-id="a5b65-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a5b65-134">Жесты руки</span><span class="sxs-lookup"><span data-stu-id="a5b65-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a5b65-135">Практические указания и фиксация</span><span class="sxs-lookup"><span data-stu-id="a5b65-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="a5b65-136">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="a5b65-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="a5b65-137">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="a5b65-137">Voice input</span></span>](voice-input.md)
