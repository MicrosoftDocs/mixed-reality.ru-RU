---
title: Взгляд
description: Взглядом является первая форма ввода и основная форма нацеливания в смешанной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Смешанный реальность, взглядом, взаимодействие, проектирование
ms.openlocfilehash: e0c1a925f6faeb37ec35e511cef36f9c06672c8a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829738"
---
# <a name="gaze"></a><span data-ttu-id="6321d-104">Взгляд</span><span class="sxs-lookup"><span data-stu-id="6321d-104">Gaze</span></span>

<span data-ttu-id="6321d-105">**Помощи** — это первая форма входных данных и является основной формой для различных версий в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="6321d-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="6321d-106">Взглядом покажет, где пользователь смотрит в мире, а также определить их назначение.</span><span class="sxs-lookup"><span data-stu-id="6321d-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="6321d-107">На практике вы обычно рассмотрим объект, который вы собираетесь взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="6321d-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="6321d-108">Это то же самое с взглядом.</span><span class="sxs-lookup"><span data-stu-id="6321d-108">This is the same with gaze.</span></span>

<span data-ttu-id="6321d-109">Смешанная реальность гарнитурах применяется положение и ориентацию головы пользователя для определения их головной взглядом вектор.</span><span class="sxs-lookup"><span data-stu-id="6321d-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="6321d-110">Этот вектор можно считать лазерную указку непосредственно перейти из напрямую между глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="6321d-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="6321d-111">Как пользователь ищет вокруг комнате, приложение может пересекаются этот луч, как с помощью свой собственный голограммы, так и с [пространственное сопоставление](spatial-mapping.md) сетки, чтобы определить, какие виртуальные или реальные объект пользователя может выглядеть.</span><span class="sxs-lookup"><span data-stu-id="6321d-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="6321d-112">На 2 HoloLens взаимодействий могут стать целью головной взглядом пользователя, взглядом глаза или рядом с помощью или гораздо передать взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="6321d-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="6321d-113">На HoloLens (1-го поколения), обычно следует создавать взаимодействия, их определения из головного взглядом пользователя, а не при визуализации или напрямую взаимодействовать в расположении вручную.</span><span class="sxs-lookup"><span data-stu-id="6321d-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="6321d-114">После запуска взаимодействия относительный движения вручную может использоваться для управления [жест](gestures.md), как и в [манипуляции или навигации](gestures.md#composite-gestures) жест.</span><span class="sxs-lookup"><span data-stu-id="6321d-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="6321d-115">С помощью иммерсивную, можно создавать решения с помощью либо головной взглядом или поддержкой указывает [движения контроллеров](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="6321d-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="6321d-116">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="6321d-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6321d-117"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="6321d-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6321d-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6321d-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6321d-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6321d-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6321d-120"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивную</strong></a></span><span class="sxs-lookup"><span data-stu-id="6321d-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6321d-121">HEAD взглядом</span><span class="sxs-lookup"><span data-stu-id="6321d-121">Head gaze</span></span></td>
        <td><span data-ttu-id="6321d-122">✔️</span><span class="sxs-lookup"><span data-stu-id="6321d-122">✔️</span></span></td>
        <td><span data-ttu-id="6321d-123">✔️</span><span class="sxs-lookup"><span data-stu-id="6321d-123">✔️</span></span></td>
        <td><span data-ttu-id="6321d-124">✔️</span><span class="sxs-lookup"><span data-stu-id="6321d-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6321d-125">Взглядом глаз</span><span class="sxs-lookup"><span data-stu-id="6321d-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="6321d-126">❌</span><span class="sxs-lookup"><span data-stu-id="6321d-126">❌</span></span></td>
        <td><span data-ttu-id="6321d-127">✔️</span><span class="sxs-lookup"><span data-stu-id="6321d-127">✔️</span></span></td>
        <td><span data-ttu-id="6321d-128">❌</span><span class="sxs-lookup"><span data-stu-id="6321d-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="6321d-129">Дополнительные рекомендации, относящиеся к HoloLens 2 [ожидается в ближайшее время](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="6321d-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="6321d-130">Варианты использования взглядом</span><span class="sxs-lookup"><span data-stu-id="6321d-130">Uses of gaze</span></span>

<span data-ttu-id="6321d-131">Как разработчик смешанной реальности для вас гораздо взглядом head или глаза:</span><span class="sxs-lookup"><span data-stu-id="6321d-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="6321d-132">Приложение может пересекаются взглядом с голограммы в сцене, чтобы определить, где находится внимания пользователя.</span><span class="sxs-lookup"><span data-stu-id="6321d-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="6321d-133">Приложения можно назначить жестов и зависимости от пользователя взглядом, позволяя пользователю выбрать, активировать, захватите, прокрутите или другим образом взаимодействовать с их голограммы нажатия контроллера.</span><span class="sxs-lookup"><span data-stu-id="6321d-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="6321d-134">Приложения можно позволить пользователю снабдить поверхностей реального мира, голограммы пересечением их Рэй взглядом в сетке пространственное сопоставление узлов.</span><span class="sxs-lookup"><span data-stu-id="6321d-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="6321d-135">Приложение может узнать, когда он *не* поиска в направлении важные объект, который можно привести приложения, чтобы предоставить звуковые и подсказки, чтобы включить для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="6321d-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="6321d-136">Cursor (Курсор)</span><span class="sxs-lookup"><span data-stu-id="6321d-136">Cursor</span></span>

<span data-ttu-id="6321d-137">Для головных взглядом большинства приложений следует использовать [курсор](cursors.md) (или другие признаки возможного аудитории/visual) для предоставления уверенность пользователей в том, что вы собираетесь взаимодействовать.</span><span class="sxs-lookup"><span data-stu-id="6321d-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="6321d-138">Как правило, этот курсор позиционирование в мире, где их луч головной взглядом сначала пересекает объект, который может быть голограмма или рабочей области реальных.</span><span class="sxs-lookup"><span data-stu-id="6321d-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="6321d-139">![Пример visual курсор для отображения взглядом](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="6321d-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="6321d-140">*Пример visual курсор для отображения взглядом*</span><span class="sxs-lookup"><span data-stu-id="6321d-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="6321d-141">Для глаз взглядом, обычно рекомендуется *не* отобразить курсора, так как это может быстро стать мешает работе и раздражающих для пользователя.</span><span class="sxs-lookup"><span data-stu-id="6321d-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="6321d-142">Вместо этого может привести к некоторой выделите visual целевые объекты или использовать курсор очень заметным глаза, чтобы обеспечить уверенность о том, что пользователь будет взаимодействовать с.</span><span class="sxs-lookup"><span data-stu-id="6321d-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="6321d-143">Дополнительные сведения, ознакомьтесь со сведениями наших [руководство по проектированию для входных данных на основе глаз](eye-tracking.md) на HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6321d-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="6321d-144">Предоставляя действие к взглядом пользователя</span><span class="sxs-lookup"><span data-stu-id="6321d-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="6321d-145">Пользователь целью голограмма или объекта реального мира, используя их взглядом, их следующим шагом после действий для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="6321d-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="6321d-146">Это основной способ для пользователя выполнить действие, выполняются через [жесты](gestures.md), [движения контроллеров](motion-controllers.md) и [голоса](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="6321d-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6321d-147">См. также</span><span class="sxs-lookup"><span data-stu-id="6321d-147">See also</span></span>
* [<span data-ttu-id="6321d-148">210. Ввод в смешанной реальности: HEAD взглядом</span><span class="sxs-lookup"><span data-stu-id="6321d-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="6321d-149">Направление головы и взгляда в DirectX</span><span class="sxs-lookup"><span data-stu-id="6321d-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="6321d-150">Взглядом HEAD в Unity</span><span class="sxs-lookup"><span data-stu-id="6321d-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="6321d-151">Отслеживания на HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6321d-151">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="6321d-152">Взглядом глаза в Unity, использование набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="6321d-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
