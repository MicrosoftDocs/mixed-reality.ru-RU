---
title: Звук в смешанной реальности
description: Звук в смешанной реальности может повысить степень уверенности пользователей в взаимодействии пользовательского интерфейса и погрузить пользователей в работу.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Пространственный звук, объемное звучание, трехмерное аудио, трехмерное звучание, Пространственный звук
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641107"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="5ba72-104">Звук в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="5ba72-104">Audio in Mixed Reality</span></span>
<span data-ttu-id="5ba72-105">Звук — это важный компонент разработки и повышения производительности в смешанной реальности, который может:</span><span class="sxs-lookup"><span data-stu-id="5ba72-105">Audio is an essential part of design and productivity in mixed reality, and can:</span></span>
* <span data-ttu-id="5ba72-106">Повышение надежности пользователей при взаимодействии на основе жестов и голоса</span><span class="sxs-lookup"><span data-stu-id="5ba72-106">Increase user confidence in gesture- and voice-based interactions</span></span>
* <span data-ttu-id="5ba72-107">Руководство пользователя о дальнейших действиях</span><span class="sxs-lookup"><span data-stu-id="5ba72-107">Guide users to next steps</span></span>
* <span data-ttu-id="5ba72-108">Эффективное объединение виртуальных объектов с реальным миром</span><span class="sxs-lookup"><span data-stu-id="5ba72-108">Effectively combine virtual objects with the real world</span></span>

<span data-ttu-id="5ba72-109">Отслеживание головных телефонов с низкой задержкой, включая HoloLens, позволяет использовать высококачественное пространственное использование ХРТФ.</span><span class="sxs-lookup"><span data-stu-id="5ba72-109">The low-latency head tracking of mixed reality headsets, including HoloLens, enables the use of high quality HRTF-based spatialization.</span></span> <span data-ttu-id="5ba72-110">Спатиализинг аудио в приложении может:</span><span class="sxs-lookup"><span data-stu-id="5ba72-110">Spatializing audio in your application can:</span></span>
* <span data-ttu-id="5ba72-111">Привлечь внимание к визуальным элементам</span><span class="sxs-lookup"><span data-stu-id="5ba72-111">Call attention to visual elements</span></span>
* <span data-ttu-id="5ba72-112">Помогите пользователям обеспечить осведомленность о реальной окружающей среде</span><span class="sxs-lookup"><span data-stu-id="5ba72-112">Help users maintain awareness of their real-world surroundings</span></span>

<span data-ttu-id="5ba72-113">Добавление акустических характеристик более глубоко соединяет голограммы со смешанным миром и может предоставлять подсказки о среде и состоянии объектов.</span><span class="sxs-lookup"><span data-stu-id="5ba72-113">Adding acoustics more deeply connects holograms to the mixed world, and can provide cues about the environment and object state.</span></span>

<span data-ttu-id="5ba72-114">Более подробные примеры проектирования с использованием аудио см. в разделе [Разработка звука](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="5ba72-114">For more detailed examples of design using audio, see [sound design](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="5ba72-115">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="5ba72-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5ba72-116"><strong>Функциями</strong></span><span class="sxs-lookup"><span data-stu-id="5ba72-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="5ba72-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="5ba72-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="5ba72-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="5ba72-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="5ba72-119"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="5ba72-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5ba72-120">Пространственный индекс</span><span class="sxs-lookup"><span data-stu-id="5ba72-120">Spatialization</span></span></td>
        <td><span data-ttu-id="5ba72-121">✔️</span><span class="sxs-lookup"><span data-stu-id="5ba72-121">✔️</span></span></td>
        <td><span data-ttu-id="5ba72-122">✔️</span><span class="sxs-lookup"><span data-stu-id="5ba72-122">✔️</span></span></td>
        <td><span data-ttu-id="5ba72-123">✔️</span><span class="sxs-lookup"><span data-stu-id="5ba72-123">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5ba72-124">Аппаратное ускорение для пространственной связи</span><span class="sxs-lookup"><span data-stu-id="5ba72-124">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="5ba72-125">✔️</span><span class="sxs-lookup"><span data-stu-id="5ba72-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a><span data-ttu-id="5ba72-126">Использование звуков в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="5ba72-126">Using sounds in mixed reality</span></span>
<span data-ttu-id="5ba72-127">[Использование звуков в смешанной реальности](spatial-sound-design.md) может потребовать иного подхода, чем в сенсорных приложениях и клавиатурах.</span><span class="sxs-lookup"><span data-stu-id="5ba72-127">[Using sounds in mixed reality](spatial-sound-design.md) can require a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="5ba72-128">Ключевые решения по проектированию звука включают в себя, какие звуки спатиализе и какие взаимодействия с сонифи.</span><span class="sxs-lookup"><span data-stu-id="5ba72-128">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="5ba72-129">Эти решения могут сильно влиять на уверенность пользователей, продуктивность и курс обучения.</span><span class="sxs-lookup"><span data-stu-id="5ba72-129">These decisions can have a strong effect on user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="5ba72-130">Практические примеры</span><span class="sxs-lookup"><span data-stu-id="5ba72-130">Case studies</span></span>
<span data-ttu-id="5ba72-131">Холотаур виртуальная пользователи таурист и исторические веб-узлы по всему миру.</span><span class="sxs-lookup"><span data-stu-id="5ba72-131">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="5ba72-132">В следующем примере описывается создание звукового дизайна для Холотаур: [звуковое проектирование для холотаур](case-study-spatial-sound-design-for-holotour.md).</span><span class="sxs-lookup"><span data-stu-id="5ba72-132">The following case study describes the sound design for HoloTour: [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md).</span></span> <span data-ttu-id="5ba72-133">Для записи предметных областей использовались специальные настройки микрофона и подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="5ba72-133">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="5ba72-134">Робораид — это кораблей высокой энергии для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5ba72-134">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="5ba72-135">В следующем примере описываются варианты проектирования, позволяющие гарантировать, что Пространственный звук использовался для полного значительного эффекта: [Создание звука для робораид](case-study-using-spatial-sound-in-roboraid.md).</span><span class="sxs-lookup"><span data-stu-id="5ba72-135">The following case study describes the design choices made to ensure spatial audio was used to fullest dramatic effect: [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span></span>

## <a name="spatialization"></a><span data-ttu-id="5ba72-136">Пространственный индекс</span><span class="sxs-lookup"><span data-stu-id="5ba72-136">Spatialization</span></span>
<span data-ttu-id="5ba72-137">Пространственные — это направленный компонент пространственного аудио.</span><span class="sxs-lookup"><span data-stu-id="5ba72-137">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="5ba72-138">При использовании настройки домашнего кинотеатра 7,1 пространственное касание — это просто панорамирование громкими динамиками.</span><span class="sxs-lookup"><span data-stu-id="5ba72-138">When using a 7.1 home theater setup, spatialization is as simple as panning between loud speakers.</span></span> <span data-ttu-id="5ba72-139">Но с наушниками в смешанной реальности очень важно использовать технологию на основе ХРТФ для точности и удобства.</span><span class="sxs-lookup"><span data-stu-id="5ba72-139">But with headphones in mixed reality it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="5ba72-140">Windows предлагает ХРТФную пространственность, и эта поддержка ускоряется с помощью аппаратного ускорения в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5ba72-140">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="5ba72-141">Я спатиализе?</span><span class="sxs-lookup"><span data-stu-id="5ba72-141">Should I spatialize?</span></span>
<span data-ttu-id="5ba72-142">Многие звуки в приложениях смешанной реальности получают преимущество от пространственности, что выводит звук из заголовка прослушивателя и помещает его в мир.</span><span class="sxs-lookup"><span data-stu-id="5ba72-142">Many sounds in mixed reality applications benefit from spatialization, which takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="5ba72-143">Рекомендации по наиболее эффективному применению пространственных данных в приложении см. в статье о [пространственном звуковом проектировании](spatial-sound-design.md) .</span><span class="sxs-lookup"><span data-stu-id="5ba72-143">Refer to [Spatial Sound Design](spatial-sound-design.md) for suggestions on the most effective uses of spatialization in your application.</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="5ba72-144">Персонализация спатиализер</span><span class="sxs-lookup"><span data-stu-id="5ba72-144">Spatializer personalization</span></span>
<span data-ttu-id="5ba72-145">Хртфс управляет различиями между уровнями и этапами между ушки в разных спектрах частот.</span><span class="sxs-lookup"><span data-stu-id="5ba72-145">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="5ba72-146">Они основаны на физических моделях и измерениях, Торсо и посвященные человеческим фигурам (пиннае).</span><span class="sxs-lookup"><span data-stu-id="5ba72-146">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="5ba72-147">Наши нервной отвечают на эти различия, чтобы подняться на восприятие направлений звука.</span><span class="sxs-lookup"><span data-stu-id="5ba72-147">Our brains respond to these differences to give rise to a perception of direction in sound.</span></span> 

<span data-ttu-id="5ba72-148">У каждого отдельного пользователя есть уникальная форма, размер и номер головного элемента, поэтому наилучшим Хртфсм являются те, которые соответствуют вам.</span><span class="sxs-lookup"><span data-stu-id="5ba72-148">Every individual has a unique ear shape, head size, and ear position, so the best HRTFs are those that conform to you.</span></span> <span data-ttu-id="5ba72-149">HoloLens повышает точность пространственности с помощью пупилариного расстояния (IPD), отображаемого на гарнитуре, чтобы настроить Хртфс для вашего головного размера.</span><span class="sxs-lookup"><span data-stu-id="5ba72-149">HoloLens increases spatialization accuracy by using your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="5ba72-150">Поддержка платформы спатиализер</span><span class="sxs-lookup"><span data-stu-id="5ba72-150">Spatializer platform support</span></span>
<span data-ttu-id="5ba72-151">Windows предлагает пространственные, в том числе Хртфс, через [API испатиалаудиоклиент](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span><span class="sxs-lookup"><span data-stu-id="5ba72-151">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="5ba72-152">Этот API обеспечивает аппаратное ускорение ХРТФ HoloLens 2 для приложений.</span><span class="sxs-lookup"><span data-stu-id="5ba72-152">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="5ba72-153">Поддержка по промежуточного слоя спатиализер</span><span class="sxs-lookup"><span data-stu-id="5ba72-153">Spatializer middleware support</span></span>
<span data-ttu-id="5ba72-154">Поддержка Windows "Хртфс" доступна для некоторых сторонних обработчиков аудио:</span><span class="sxs-lookup"><span data-stu-id="5ba72-154">Support for Windows' HRTFs is available for some 3rd-party audio engines:</span></span>
* <span data-ttu-id="5ba72-155">Подключаемый модуль [обработчика звука Unity](spatial-sound-in-unity.md) вызывает хртф ксапо</span><span class="sxs-lookup"><span data-stu-id="5ba72-155">A [Unity audio engine](spatial-sound-in-unity.md) plugin calls the HRTF XAPO</span></span>
* <span data-ttu-id="5ba72-156">[Подключаемый модуль ввисе Audio Engine](https://www.audiokinetic.com/products/plug-ins/msspatial/) вызывает API испатиалаудиоклиент.</span><span class="sxs-lookup"><span data-stu-id="5ba72-156">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/) calls the ISpatialAudioClient API</span></span>

## <a name="acoustics"></a><span data-ttu-id="5ba72-157">Акустические характеристики</span><span class="sxs-lookup"><span data-stu-id="5ba72-157">Acoustics</span></span>
<span data-ttu-id="5ba72-158">Пространственный звук может быть около направления.</span><span class="sxs-lookup"><span data-stu-id="5ba72-158">Spatial audio can be about more than direction.</span></span> <span data-ttu-id="5ba72-159">Другие измерения, включая перекрытия, препятствия, переглаголы, порталлинг и модель источника, совместно называются "акустическими".</span><span class="sxs-lookup"><span data-stu-id="5ba72-159">Other dimensions, including occlusion, obstruction, reverb, portalling, and source modelling, are collectively referred to as 'acoustics'.</span></span> <span data-ttu-id="5ba72-160">Без акустических сигналов пространственные звуки не имеют воспринимаемого расстояния.</span><span class="sxs-lookup"><span data-stu-id="5ba72-160">Without acoustics, spatialized sounds lack a perceived distance.</span></span>

<span data-ttu-id="5ba72-161">Обработка акустических характеристик может варьироваться от простых до очень сложных.</span><span class="sxs-lookup"><span data-stu-id="5ba72-161">Acoustics treatment can range from simple to very complex.</span></span> <span data-ttu-id="5ba72-162">Используя простую перекоманду, например, поддерживаемую любой подсистемой аудио, можно передать пространственные звуки в среду, окружающую прослушиватель.</span><span class="sxs-lookup"><span data-stu-id="5ba72-162">By using a simple reverb, such as that supported by any audio engine, you can push spatialized sounds out into the environment surrounding the listener.</span></span> <span data-ttu-id="5ba72-163">Улучшенная и более привлекательная обработка акустических характеристик доступна в таких системах, как [акустические характеристики проекта](https://aka.ms/acoustics).</span><span class="sxs-lookup"><span data-stu-id="5ba72-163">Richer and more compelling acoustics treatment is available from acoustics systems such as [Project Acoustics](https://aka.ms/acoustics).</span></span> <span data-ttu-id="5ba72-164">Акустика проекта может моделировать воздействие стен, дверей и других геометрических объектов сцены на звук и является эффективным вариантом для случаев, когда соответствующая геометрия сцены известна во время разработки.</span><span class="sxs-lookup"><span data-stu-id="5ba72-164">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound, and is an effective option for cases where the relevant scene geometry is known at development time.</span></span>

