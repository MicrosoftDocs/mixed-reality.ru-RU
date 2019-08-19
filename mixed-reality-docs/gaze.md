---
title: Взгляд
description: Взгляд — это первая форма входных данных, которая является основной формой нацеливания в смешанной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Смешанная реальность, взгляд, взаимодействие, проектирование
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414370"
---
# <a name="gaze"></a><span data-ttu-id="2b4aa-104">Взгляд</span><span class="sxs-lookup"><span data-stu-id="2b4aa-104">Gaze</span></span>

<span data-ttu-id="2b4aa-105">**Взгляд** — это первая форма входных данных, которая является основной формой нацеливания в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="2b4aa-106">Посмотрите, где пользователь смотрит в мире и позволяет определить их намерение.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="2b4aa-107">В реальном мире вы обычно просматриваете объект, с которым планируется взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="2b4aa-108">Это аналогично с помощью взгляда.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-108">This is the same with gaze.</span></span>

<span data-ttu-id="2b4aa-109">Гарнитуры смешанной реальности используют положение и ориентацию заголовка пользователя, чтобы определить вектор взгляда на голову.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="2b4aa-110">Этот вектор можно представить себе как лазерный указатель непосредственно между глазами пользователя.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="2b4aa-111">По мере того как пользователь смотрит комнату, приложение может пересекать этот луч как с собственными голограммами, так и с сеткой [пространственного сопоставления](spatial-mapping.md) , чтобы определить, какой объект может найти пользователь.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="2b4aa-112">В HoloLens 2 взаимодействие может быть нацелено на головное взгляд пользователя, взгляд глаз или с помощью практически или дальнего взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="2b4aa-113">В HoloLens (1-й Gen) взаимодействия обычно должны наследовать нацеливание от заголовков пользователя, а не пытаться напрямую отрисовываться или взаимодействовать в расположении руки.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="2b4aa-114">После запуска взаимодействия можно использовать относительные движения руки для управления [жестом](gestures.md), как в случае манипуляции или жеста [навигации](gestures.md#composite-gestures) .</span><span class="sxs-lookup"><span data-stu-id="2b4aa-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="2b4aa-115">С помощью впечатляющих головных телефонов вы можете ориентироваться на [контроллеры движения](motion-controllers.md)с головным взглядом или с поддержкой курсоров.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="2b4aa-116">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="2b4aa-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2b4aa-117"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="2b4aa-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="2b4aa-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2b4aa-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2b4aa-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2b4aa-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2b4aa-120"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="2b4aa-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2b4aa-121">Взгляд на голову</span><span class="sxs-lookup"><span data-stu-id="2b4aa-121">Head gaze</span></span></td>
        <td><span data-ttu-id="2b4aa-122">✔️</span><span class="sxs-lookup"><span data-stu-id="2b4aa-122">✔️</span></span></td>
        <td><span data-ttu-id="2b4aa-123">✔️</span><span class="sxs-lookup"><span data-stu-id="2b4aa-123">✔️</span></span></td>
        <td><span data-ttu-id="2b4aa-124">✔️</span><span class="sxs-lookup"><span data-stu-id="2b4aa-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2b4aa-125">Взгляд глаз</span><span class="sxs-lookup"><span data-stu-id="2b4aa-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="2b4aa-126">❌</span><span class="sxs-lookup"><span data-stu-id="2b4aa-126">❌</span></span></td>
        <td><span data-ttu-id="2b4aa-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2b4aa-127">✔️</span></span></td>
        <td><span data-ttu-id="2b4aa-128">❌</span><span class="sxs-lookup"><span data-stu-id="2b4aa-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="2b4aa-129">В [ближайшее время ожидается](index.md#news-and-notes)более подробное руководство по HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="2b4aa-130">Использование взгляда</span><span class="sxs-lookup"><span data-stu-id="2b4aa-130">Uses of gaze</span></span>

<span data-ttu-id="2b4aa-131">Как разработчик смешанной реальности вы можете сделать многое с взглядом на голову:</span><span class="sxs-lookup"><span data-stu-id="2b4aa-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="2b4aa-132">Ваше приложение может быть пересекается с голограммами в сцене, чтобы определить, где это внимание уделяется пользователю.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="2b4aa-133">Приложение может нацелить жесты и нажимать контроллер на основе взгляда пользователя, позволяя пользователю выбирать, активировать, захватить, прокручивать или иным способом взаимодействовать с их голограммами.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="2b4aa-134">Приложение может позволить пользователю размещать голограммы на реальных поверхностях, пересекать их лучом с помощью сетки пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="2b4aa-135">Приложение может быть уверенным в том, что пользователь *не* смотрит в направлении важного объекта, что может привести к тому, что ваше приложение предоставит визуальные и звуковые подсказки для включения этого объекта.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="2b4aa-136">Cursor (Курсор)</span><span class="sxs-lookup"><span data-stu-id="2b4aa-136">Cursor</span></span>

<span data-ttu-id="2b4aa-137">Для головного взгляда в большинстве приложений следует использовать [курсор](cursors.md) (или другой индикатор аудита или визуального отображения), чтобы дать пользователю уверенность в том, с чем они взаимодействуют.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="2b4aa-138">Как правило, этот курсор размещается в мире, где первый из них сначала пересекает объект, что может быть голограммой или реальной поверхностью.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="2b4aa-139">![Пример визуального курсора для отображения взгляда](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="2b4aa-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="2b4aa-140">*Пример визуального курсора для отображения взгляда*</span><span class="sxs-lookup"><span data-stu-id="2b4aa-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="2b4aa-141">Для глаза, как правило, рекомендуется *не* отображать курсор, так как это может быстро стать нежелательным и непонятным для пользователя.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="2b4aa-142">Вместо этого можно выделить визуальные целевые объекты или использовать очень бледный курсор, чтобы предоставить уверенность о том, с чем будет взаимодействовать пользователь.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="2b4aa-143">Дополнительные сведения см. в нашем руководстве по [проектированию для получения данных на основе глаз](eye-tracking.md) в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="2b4aa-144">Предоставление действия пользователю</span><span class="sxs-lookup"><span data-stu-id="2b4aa-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="2b4aa-145">После того как пользователь назначит голограмму или реальный объект с помощью взгляда, следующим шагом будет выполнение действий с этим объектом.</span><span class="sxs-lookup"><span data-stu-id="2b4aa-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="2b4aa-146">Основные способы выполнения действий пользователем — [жесты](gestures.md), [контроллеры движения](motion-controllers.md) и [голоса](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="2b4aa-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b4aa-147">См. также</span><span class="sxs-lookup"><span data-stu-id="2b4aa-147">See also</span></span>
* [<span data-ttu-id="2b4aa-148">210. Ввод в смешанной реальности: Взгляд на голову</span><span class="sxs-lookup"><span data-stu-id="2b4aa-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="2b4aa-149">Направление головы и взгляда в DirectX</span><span class="sxs-lookup"><span data-stu-id="2b4aa-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="2b4aa-150">Головное взгляд в Unity</span><span class="sxs-lookup"><span data-stu-id="2b4aa-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="2b4aa-151">Глаз — Взгляните на HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2b4aa-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="2b4aa-152">Взгляд глаз в Unity с помощью набора средств Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2b4aa-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
