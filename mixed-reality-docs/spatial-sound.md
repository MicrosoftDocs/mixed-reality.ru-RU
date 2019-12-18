---
title: Звук в смешанной реальности
description: Звук в смешанной реальности может повысить степень уверенности пользователей в взаимодействии пользовательского интерфейса и погрузить пользователей в работу.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Пространственный звук, объемное звучание, трехмерное аудио, трехмерное звучание, Пространственный звук
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181984"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="1f215-104">Звук в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="1f215-104">Audio in mixed reality</span></span>
<span data-ttu-id="1f215-105">Звук является важнейшей частью проектирования и повышения производительности в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1f215-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="1f215-106">Звук может:</span><span class="sxs-lookup"><span data-stu-id="1f215-106">Sound can:</span></span>
* <span data-ttu-id="1f215-107">Повысьте уверенность пользователей в жестах и голосовом взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="1f215-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="1f215-108">Руководство пользователя к дальнейшим действиям.</span><span class="sxs-lookup"><span data-stu-id="1f215-108">Guide users to next steps.</span></span>
* <span data-ttu-id="1f215-109">Эффективно объединять виртуальные объекты с реальным миром.</span><span class="sxs-lookup"><span data-stu-id="1f215-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="1f215-110">Отслеживание головных головных телефонов с низкой задержкой, включая HoloLens, поддерживает высококачественное пространственное ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="1f215-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="1f215-111">Вы можете спатиализе звук в приложении, чтобы:</span><span class="sxs-lookup"><span data-stu-id="1f215-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="1f215-112">Привлечь внимание к визуальным элементам.</span><span class="sxs-lookup"><span data-stu-id="1f215-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="1f215-113">Помогите пользователям обеспечить осведомленность о реальной окружающей среде.</span><span class="sxs-lookup"><span data-stu-id="1f215-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="1f215-114">Акустические сведения более глубоко присоединяются к миру смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1f215-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="1f215-115">Он предоставляет подсказки о среде и состоянии объектов.</span><span class="sxs-lookup"><span data-stu-id="1f215-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="1f215-116">См. подробные [Примеры проектирования, в которых используется аудио](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="1f215-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="1f215-117">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="1f215-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1f215-118"><strong>Возможность</strong></span><span class="sxs-lookup"><span data-stu-id="1f215-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1f215-119"><a href="hololens-hardware-details.md"><strong>HoloLens (первый общий)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1f215-119"><a href="hololens-hardware-details.md"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1f215-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1f215-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1f215-121"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="1f215-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1f215-122">Пространственный индекс</span><span class="sxs-lookup"><span data-stu-id="1f215-122">Spatialization</span></span></td>
        <td><span data-ttu-id="1f215-123">✔️</span><span class="sxs-lookup"><span data-stu-id="1f215-123">✔️</span></span></td>
        <td><span data-ttu-id="1f215-124">✔️</span><span class="sxs-lookup"><span data-stu-id="1f215-124">✔️</span></span></td>
        <td><span data-ttu-id="1f215-125">✔️</span><span class="sxs-lookup"><span data-stu-id="1f215-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1f215-126">Аппаратное ускорение для пространственной связи</span><span class="sxs-lookup"><span data-stu-id="1f215-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="1f215-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1f215-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="1f215-128">Использование звуков в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="1f215-128">Use of sounds in mixed reality</span></span>
<span data-ttu-id="1f215-129">[Использование звуков в смешанной реальности](spatial-sound-design.md) требует иного подхода, чем в приложениях для сенсорного ввода и мыши.</span><span class="sxs-lookup"><span data-stu-id="1f215-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="1f215-130">Ключевые решения по проектированию звука включают в себя, какие звуки спатиализе и какие взаимодействия с сонифи.</span><span class="sxs-lookup"><span data-stu-id="1f215-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="1f215-131">Эти решения сильно влияют на уверенность пользователей, продуктивность и курс обучения.</span><span class="sxs-lookup"><span data-stu-id="1f215-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="1f215-132">Практические примеры</span><span class="sxs-lookup"><span data-stu-id="1f215-132">Case studies</span></span>
<span data-ttu-id="1f215-133">Холотаур виртуальная пользователи таурист и исторические веб-узлы по всему миру.</span><span class="sxs-lookup"><span data-stu-id="1f215-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="1f215-134">Ознакомьтесь со статьей « [звук» для](case-study-spatial-sound-design-for-holotour.md) примера внедрения холотаур.</span><span class="sxs-lookup"><span data-stu-id="1f215-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="1f215-135">Для записи предметных областей использовались специальные настройки микрофона и подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="1f215-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="1f215-136">Робораид — это кораблей высокой энергии для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1f215-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="1f215-137">В примере « [звук» для](case-study-using-spatial-sound-in-roboraid.md) примера использования робораид описываются варианты проектирования, которые позволяют обеспечить использование пространственного звука для полного значительного эффекта.</span><span class="sxs-lookup"><span data-stu-id="1f215-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="1f215-138">Пространственный индекс</span><span class="sxs-lookup"><span data-stu-id="1f215-138">Spatialization</span></span>
<span data-ttu-id="1f215-139">Пространственные — это направленный компонент пространственного аудио.</span><span class="sxs-lookup"><span data-stu-id="1f215-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="1f215-140">Для настройки домашнего кинотеатра 7,1 Пространственное преобразование осуществляется так же просто, как панорамирование между лаудспеакерс.</span><span class="sxs-lookup"><span data-stu-id="1f215-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="1f215-141">Но для наушников в смешанной реальности очень важно использовать технологию на основе ХРТФ для точности и удобства.</span><span class="sxs-lookup"><span data-stu-id="1f215-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="1f215-142">Windows предлагает ХРТФную пространственность, и эта поддержка ускоряется с помощью аппаратного ускорения в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1f215-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="1f215-143">Я спатиализе?</span><span class="sxs-lookup"><span data-stu-id="1f215-143">Should I spatialize?</span></span>
<span data-ttu-id="1f215-144">Пространственный способ улучшить многие звуки в приложениях смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="1f215-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="1f215-145">При пространственной деставится звук из заголовка прослушивателя и он помещается в мир.</span><span class="sxs-lookup"><span data-stu-id="1f215-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="1f215-146">Рекомендации по эффективному использованию пространственного использования в приложении см. в разделе [проектирование пространственного звука](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="1f215-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="1f215-147">Персонализация спатиализер</span><span class="sxs-lookup"><span data-stu-id="1f215-147">Spatializer personalization</span></span>
<span data-ttu-id="1f215-148">Хртфс управляет различиями между уровнями и этапами между ушки в разных спектрах частот.</span><span class="sxs-lookup"><span data-stu-id="1f215-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="1f215-149">Они основаны на физических моделях и измерениях, Торсо и посвященные человеческим фигурам (пиннае).</span><span class="sxs-lookup"><span data-stu-id="1f215-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="1f215-150">Наш нервной отвечает на эти различия, чтобы обеспечить восприятное направление звука.</span><span class="sxs-lookup"><span data-stu-id="1f215-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="1f215-151">Каждый пользователь имеет уникальную форму «год», размер головного элемента и «год».</span><span class="sxs-lookup"><span data-stu-id="1f215-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="1f215-152">Итак, лучший Хртфс соответствует вам.</span><span class="sxs-lookup"><span data-stu-id="1f215-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="1f215-153">Чтобы повысить точность пространственности, HoloLens использует пупилари расстояние (IPD), отображаемое на гарнитуре, чтобы настроить Хртфс для вашего головного размера.</span><span class="sxs-lookup"><span data-stu-id="1f215-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="1f215-154">Поддержка платформы спатиализер</span><span class="sxs-lookup"><span data-stu-id="1f215-154">Spatializer platform support</span></span>
<span data-ttu-id="1f215-155">Windows предлагает пространственные, в том числе Хртфс, через [API испатиалаудиоклиент](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span><span class="sxs-lookup"><span data-stu-id="1f215-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="1f215-156">Этот API обеспечивает аппаратное ускорение ХРТФ HoloLens 2 для приложений.</span><span class="sxs-lookup"><span data-stu-id="1f215-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="1f215-157">Поддержка по промежуточного слоя спатиализер</span><span class="sxs-lookup"><span data-stu-id="1f215-157">Spatializer middleware support</span></span>
<span data-ttu-id="1f215-158">Поддержка Windows "Хртфс" доступна для следующих сторонних обработчиков аудио.</span><span class="sxs-lookup"><span data-stu-id="1f215-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="1f215-159">[Подключаемый модуль механизма обработки речи Unity](spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="1f215-159">A [Unity audio engine plugin](spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="1f215-160">[Подключаемый модуль ввисе Audio Engine](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span><span class="sxs-lookup"><span data-stu-id="1f215-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="1f215-161">Акустические характеристики</span><span class="sxs-lookup"><span data-stu-id="1f215-161">Acoustics</span></span>
<span data-ttu-id="1f215-162">Пространственный звук больше, чем направление.</span><span class="sxs-lookup"><span data-stu-id="1f215-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="1f215-163">К другим измерениям относятся перекрытия, препятствия, переглаголы, порталлинг и моделирование исходного кода.</span><span class="sxs-lookup"><span data-stu-id="1f215-163">Other dimensions include occlusion, obstruction, reverb, portalling, and source modeling.</span></span> <span data-ttu-id="1f215-164">Вместе эти измерения называются *акустическими*.</span><span class="sxs-lookup"><span data-stu-id="1f215-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="1f215-165">Без акустических сигналов пространственные звуки не имеют воспринимаемого расстояния.</span><span class="sxs-lookup"><span data-stu-id="1f215-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="1f215-166">Акустические использование в диапазоне от простого до очень сложного.</span><span class="sxs-lookup"><span data-stu-id="1f215-166">Acoustics treatments range from simple to very complex.</span></span> <span data-ttu-id="1f215-167">Вы можете использовать простую команду, которая поддерживается любым обработчиком аудио, чтобы отправлять пространственные звуки в среду прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="1f215-167">You can use a simple reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="1f215-168">Системы акустических характеристик, такие как [акустические характеристики проекта](https://aka.ms/acoustics) , обеспечивают более широкие и привлекательные акустические характеристики.</span><span class="sxs-lookup"><span data-stu-id="1f215-168">Acoustics systems such as [Project Acoustics](https://aka.ms/acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="1f215-169">Акустика проекта может моделировать воздействие стен, дверей и другой геометрии сцены на звук.</span><span class="sxs-lookup"><span data-stu-id="1f215-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="1f215-170">Это эффективный вариант для случаев, когда соответствующая геометрия сцены известна во время разработки.</span><span class="sxs-lookup"><span data-stu-id="1f215-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f215-171">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="1f215-171">Next steps</span></span>
- [<span data-ttu-id="1f215-172">Пространственный звук в Unity</span><span class="sxs-lookup"><span data-stu-id="1f215-172">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
- [<span data-ttu-id="1f215-173">Использование звука в приложениях смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="1f215-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)
