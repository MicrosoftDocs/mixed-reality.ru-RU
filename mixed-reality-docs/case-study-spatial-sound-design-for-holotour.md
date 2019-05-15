---
title: Пример использования - пространственных систему для HoloTour
description: Чтобы создать по-настоящему иммерсивных трехмерных виртуальный Обзор для Microsoft HoloLens, панорамное видео и holographic ландшафт Вот лишь небольшая часть формулы.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, HoloTour, пространственных звука, вариантов использования
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603640"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a><span data-ttu-id="66ae8-104">Пример использования - пространственных систему для HoloTour</span><span class="sxs-lookup"><span data-stu-id="66ae8-104">Case study - Spatial sound design for HoloTour</span></span>

<span data-ttu-id="66ae8-105">Чтобы создать по-настоящему иммерсивных трехмерных виртуальный Обзор для Microsoft HoloLens, панорамное видео и holographic ландшафт Вот лишь небольшая часть формулы.</span><span class="sxs-lookup"><span data-stu-id="66ae8-105">To create a truly immersive 3D virtual tour for Microsoft HoloLens, the panoramic videos and holographic scenery are only part of the formula.</span></span> <span data-ttu-id="66ae8-106">Джейсон Syltebo рассказывает о том, как звука аудио конструктора был сбора и обработки в качестве почувствовать себя фактически в каждом из расположений в HoloTour.</span><span class="sxs-lookup"><span data-stu-id="66ae8-106">Audio designer Jason Syltebo talks about how sound was captured and processed to make you feel like you're actually in each of the locations in HoloTour.</span></span>

## <a name="the-tech"></a><span data-ttu-id="66ae8-107">Технический</span><span class="sxs-lookup"><span data-stu-id="66ae8-107">The tech</span></span>

<span data-ttu-id="66ae8-108">Визуально привлекательные изображения и holographic сцен в HoloTour являются лишь одна сторона создает интерфейс проверите смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="66ae8-108">The beautiful imagery and holographic scenes you see in HoloTour are only one part of creating a believable mixed reality experience.</span></span> <span data-ttu-id="66ae8-109">Хотя голограммы может использоваться только в визуальном режиме перед пользователем, [пространственных звук](spatial-sound.md) функция HoloLens позволяет аудио из всех направлениях, что дает пользователю возможность более полный экстрасенсорное.</span><span class="sxs-lookup"><span data-stu-id="66ae8-109">While holograms can only appear visually in front of a user, the [spatial sound](spatial-sound.md) feature of HoloLens allows audio to come from all directions, which gives the user a more complete sensory experience.</span></span>

<span data-ttu-id="66ae8-110">Пространственные звук позволяет нам предоставить аудиоподсказок для указания направления, в котором пользователь должен включать, или позволить пользователю, что существуют дополнительные голограммы их в своем пространстве.</span><span class="sxs-lookup"><span data-stu-id="66ae8-110">Spatial sound allows us to give audio cues to indicate a direction in which the user should turn, or to let the user know there are more holograms for them to see within their space.</span></span> <span data-ttu-id="66ae8-111">Можно также присоединить звука непосредственно к голограмма и постоянно обновляет направление и расстояние, она состоит из пользователей, чтобы создать ощущение, как если звук поступает непосредственно из этого объекта.</span><span class="sxs-lookup"><span data-stu-id="66ae8-111">We can also attach a sound directly to a hologram and continually update the direction and distance the hologram is from a user to make it seem as if the sound is coming directly from that object.</span></span>

<span data-ttu-id="66ae8-112">С помощью HoloTour мы хотели воспользоваться преимуществами пространственного звуковые возможности HoloLens для создания внешней среды 360 градусов, синхронизируется с видео, чтобы показать основные особенности sonic определенных расположений.</span><span class="sxs-lookup"><span data-stu-id="66ae8-112">With HoloTour, we wanted to take advantage of the spatial sound capabilities of HoloLens to create a 360-degree ambient environment, synchronized with the video to reveal the sonic highlights of specific locations.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="66ae8-113">Как это делается</span><span class="sxs-lookup"><span data-stu-id="66ae8-113">Behind the scenes</span></span>

<span data-ttu-id="66ae8-114">Мы создали HoloTour интерфейсы из двух разных расположений: Рим и Machu Picchu.</span><span class="sxs-lookup"><span data-stu-id="66ae8-114">We created HoloTour experiences of two different locations: Rome and Machu Picchu.</span></span> <span data-ttu-id="66ae8-115">Чтобы сделать эти учебники, которые вы, подлинность и привлекательные, мы хотели Избегайте использования универсальных звуки и вместо этого запись звука непосредственно из расположения, где мы съемки.</span><span class="sxs-lookup"><span data-stu-id="66ae8-115">To make these tours feel authentic and compelling we wanted to avoid using generic sounds and instead capture audio directly from the locations where we were filming.</span></span>

### <a name="capturing-the-audio"></a><span data-ttu-id="66ae8-116">Записи звука</span><span class="sxs-lookup"><span data-stu-id="66ae8-116">Capturing the audio</span></span>

<span data-ttu-id="66ae8-117">В нашем [практический пример о записи визуального содержимого для HoloTour](case-study-capturing-and-creating-content-for-holotour.md), мы говорили о проектировании пользовательских нашей платформе камеры.</span><span class="sxs-lookup"><span data-stu-id="66ae8-117">In our [case study about capturing the visual content for HoloTour](case-study-capturing-and-creating-content-for-holotour.md), we talked about the custom design of our camera rig.</span></span> <span data-ttu-id="66ae8-118">Это решение состояло из 14 GoPro камеры, содержащихся в корпус, трехмерной печати, предназначенных для определенных размеров штатива.</span><span class="sxs-lookup"><span data-stu-id="66ae8-118">It consisted of 14 GoPro cameras contained in a 3D-printed housing, designed to the specific dimensions of the tripod.</span></span> <span data-ttu-id="66ae8-119">Для записи звукового сигнала при помощи этой платформы, мы добавили четыре микрофон, под камеры, которые переданы в блок compact записи 4-канал, который сидел в основании штатива.</span><span class="sxs-lookup"><span data-stu-id="66ae8-119">To capture audio from this rig, we added a quad-microphone array beneath the cameras, which fed into a compact 4-channel recording unit that sat at the base of the tripod.</span></span> <span data-ttu-id="66ae8-120">Мы выбрали микрофонов, не выполнена только хорошо, но которой есть очень незначительный объем, таким образом, чтобы не скрывать представления камеры.</span><span class="sxs-lookup"><span data-stu-id="66ae8-120">We chose microphones that not only performed well, but which had a very small footprint, so as to not occlude the view of the camera.</span></span>

<span data-ttu-id="66ae8-121">![Пользовательские камеру и микрофон тестовой платформы](images/camera-rig-microphones-300px.png)</span><span class="sxs-lookup"><span data-stu-id="66ae8-121">![Custom camera and microphone rig](images/camera-rig-microphones-300px.png)</span></span><br>
<span data-ttu-id="66ae8-122">*Пользовательские камеру и микрофон тестовой платформы*</span><span class="sxs-lookup"><span data-stu-id="66ae8-122">*Custom camera and microphone rig*</span></span>

<span data-ttu-id="66ae8-123">Эта настройка захвата звука в четыре разных направления из точное расположение наших камеры, что дает нам достаточно информации для повторного создания трехмерных звуковую панорамы с помощью пространственных звук колокольчика, который мы позже удалось синхронизовать с видео 360 градусов.</span><span class="sxs-lookup"><span data-stu-id="66ae8-123">This setup captured sound in four directions from the precise location of our camera, giving us enough information to re-create a 3D aural panorama using spatial sound, which we could later synchronize to the 360-degree video.</span></span>

<span data-ttu-id="66ae8-124">Одной из проблем со звуком массива камеры является зависели от записанным во время записи.</span><span class="sxs-lookup"><span data-stu-id="66ae8-124">One of the challenges with the camera array audio is that you are at the mercy of what is recorded at the time of capture.</span></span> <span data-ttu-id="66ae8-125">Даже если видеозаписи достаточно хороша, захвата звука может стать проблематично из-за отключение камеры звуки, такие как сирену, самолете или высокой подойдет к концу.</span><span class="sxs-lookup"><span data-stu-id="66ae8-125">Even if the video capture is good, the sound capture can become problematic due to off-camera sounds such as sirens, airplanes, or high winds.</span></span> <span data-ttu-id="66ae8-126">Гарантировать, что все элементы, которые нужны, мы использовали несколько разделов стерео и mono мобильных записи для получения элементов асинхронные, окружающей среды в определенные моменты интерес в каждом расположении.</span><span class="sxs-lookup"><span data-stu-id="66ae8-126">To assure we had all the elements we need, we used a series of stereo and mono mobile recording units to get asynchronous, ambient elements at specific points of interest in each location.</span></span> <span data-ttu-id="66ae8-127">Эта запись является важным, поскольку он даст возможность поиска план в четком и использовать содержимое, которое может использоваться в эксплуатации для быстрого создания интересов и добавление дополнительных направленность звуковой конструктора.</span><span class="sxs-lookup"><span data-stu-id="66ae8-127">This capture is important as it gives the sound designer the ability to seek out clean and usable content that can be used in post-production to craft interest and add further directionality.</span></span>

<span data-ttu-id="66ae8-128">Любой день в данной записи вызовет большое количество файлов.</span><span class="sxs-lookup"><span data-stu-id="66ae8-128">Any given capture day would generate a large number of files.</span></span> <span data-ttu-id="66ae8-129">Было важно разработать систему для отслеживания, какие файлы соответствуют определенного расположения или камеры снимок.</span><span class="sxs-lookup"><span data-stu-id="66ae8-129">It was important to develop a system to track which files correspond to a particular location or camera shot.</span></span> <span data-ttu-id="66ae8-130">Модульного записи был настройки предусматривают автоматически имя файлов по дате и число take и мы бы резервную в конце дня для внешних дисках.</span><span class="sxs-lookup"><span data-stu-id="66ae8-130">Our recording unit was set up to auto-name files by date and take number and we would back these up at the end of the day to external drives.</span></span> <span data-ttu-id="66ae8-131">По крайней мере словесно slating начало аудиозаписи был важны, так как это позволяет легко идентифицировать контекстно-зависимое содержимое, имена файлов должны стать проблемой.</span><span class="sxs-lookup"><span data-stu-id="66ae8-131">At the very least, verbally slating the beginning of audio recordings was important as this allows easy contextual identification of the content should filenames become a problem.</span></span> <span data-ttu-id="66ae8-132">Также было возможность визуально синевато тестовой платформы камеры, аудио и видео, регистрируются как отдельный носитель и необходимые для синхронизации во время post.</span><span class="sxs-lookup"><span data-stu-id="66ae8-132">It was also important for us to visually slate the camera rig capture as the video and audio were recorded as separate media and needed to be synchronized during post.</span></span>

### <a name="editing-the-audio"></a><span data-ttu-id="66ae8-133">Изменение звукового файла</span><span class="sxs-lookup"><span data-stu-id="66ae8-133">Editing the audio</span></span>

<span data-ttu-id="66ae8-134">Обратно в studio после обработки записи является первым шагом для компоновки направления и иммерсивных воспроизведением звукового Чтобы просмотреть все записи звука для location: Выбор наиболее принимает и определяющее все основные особенности, которые могли быть применены творчески во время Интеграция.</span><span class="sxs-lookup"><span data-stu-id="66ae8-134">Back at the studio after the capture trip, the first step in assembling a directional and immersive aural experience is to review all of the audio capture for a location, picking out the best takes and identifying any highlights that could be applied creatively during integration.</span></span> <span data-ttu-id="66ae8-135">Затем аудио редактировать и очищены.</span><span class="sxs-lookup"><span data-stu-id="66ae8-135">The audio is then edited and cleaned up.</span></span> <span data-ttu-id="66ae8-136">Например horn громкий автомобиля, продолжающийся секунды или около того и повторное выполнение несколько раз, можно заменить и присоединения с помощью разделов quiet, внешней звукового сигнала при помощи ту же запись пакетов.</span><span class="sxs-lookup"><span data-stu-id="66ae8-136">For example, a loud car horn lasting a second or so and repeating a few times, can be replaced and stitched in with sections of quiet, ambient audio from the same capture.</span></span>

<span data-ttu-id="66ae8-137">После установления редактирования видео для расположения звуковой конструктора можно синхронизировать соответствующее аудио.</span><span class="sxs-lookup"><span data-stu-id="66ae8-137">Once the video edit for a location has been established the sound designer can synchronize the corresponding audio.</span></span> <span data-ttu-id="66ae8-138">На этом этапе мы сотрудничаем с камеры тестовой платформы и мобильных записи, чтобы решить, какие элементы или комбинации, будет работать для сборки иммерсивных аудио сцены.</span><span class="sxs-lookup"><span data-stu-id="66ae8-138">At this point we worked with both camera rig capture and mobile capture to decide what elements, or combination thereof, will work to build an immersive audio scene.</span></span> <span data-ttu-id="66ae8-139">Способ, мы обнаружили, полезно было необходимо добавить все элементы звука в аудио редактора и построения быстрый линейный макетов ИБП поэкспериментировать с разным идеи.</span><span class="sxs-lookup"><span data-stu-id="66ae8-139">A technique we found useful was to add all the sound elements into an audio editor and build quick linear mock ups to experiment with different mix ideas.</span></span> <span data-ttu-id="66ae8-140">Это дало нам лучше формат идеи когда пришло время для создания фактического HoloTour автоматически.</span><span class="sxs-lookup"><span data-stu-id="66ae8-140">This gave us better formed ideas when it came time to build the actual HoloTour scenes.</span></span>

### <a name="assembling-the-scene"></a><span data-ttu-id="66ae8-141">Сборка сцены</span><span class="sxs-lookup"><span data-stu-id="66ae8-141">Assembling the scene</span></span>

<span data-ttu-id="66ae8-142">Первым шагом в создании трехмерной сцены окружения является создание испытательной общего характера окружения циклическое звуков, которые будут поддерживать других функций и интерактивные звуковой элементы в сцене.</span><span class="sxs-lookup"><span data-stu-id="66ae8-142">The first step to building a 3D ambient scene is to create a bed of general background ambient looping sounds that will support other features and interactive sound elements in a scene.</span></span> <span data-ttu-id="66ae8-143">Таким образом, мы воспользовались целостный подход к разные реализации методов, определяется требованиями и требованиями к проекту любой конкретной сцены.</span><span class="sxs-lookup"><span data-stu-id="66ae8-143">In doing so, we took a holistic approach towards different implementation techniques determined by the specific needs and design criteria of any particular scene.</span></span> <span data-ttu-id="66ae8-144">Некоторые сцены может быть индексом с помощью записи синхронизированной камеры, тогда как другие могут требовать более проверенный подход, который использует более отдельности поместить звуков, интерактивных элементов и музыкальные и звуковые эффекты для более возможности секунд в HoloTour.</span><span class="sxs-lookup"><span data-stu-id="66ae8-144">Some scenes might index towards using the synchronized camera capture, whereas others might require a more curated approach that uses more discretely placed sounds, interactive elements and music and sound effects for the more cinematic moments in HoloTour.</span></span>

<span data-ttu-id="66ae8-145">При индексировании по использованию записи звука камеры, мы разместили пространственных поддержкой звука окружающей среды аудио отправители соответствующий направления координаты ориентацию камеры таким образом, что представления камеры Северной воспроизводится аудио с микрофона Северной и точно так же другие фундаментальный направлений.</span><span class="sxs-lookup"><span data-stu-id="66ae8-145">When indexing on the use of the camera capture audio, we placed spatial sound-enabled ambient audio emitters corresponding to the directional coordinates of the camera orientation such that the north camera view plays audio from the north microphone and likewise for the other cardinal directions.</span></span> <span data-ttu-id="66ae8-146">Эти отправители довольно заблокированы в мире, пользователь может свободно включить их головах относительно этих отправители и звук изменится соответствующим образом, фактически моделирования звук положение в этом расположении.</span><span class="sxs-lookup"><span data-stu-id="66ae8-146">These emitters are world-locked, meaning the user can freely turn their head in relation to these emitters and the sound will change accordingly, effectively modeling the sound of standing at that location.</span></span> <span data-ttu-id="66ae8-147">Прослушивать Piazza Navona или Pantheon примеры сцен, использовать хорошее сочетание камеры записи аудио.</span><span class="sxs-lookup"><span data-stu-id="66ae8-147">Listen to Piazza Navona or The Pantheon for examples of scenes that use a good mix of camera captured audio.</span></span>

<span data-ttu-id="66ae8-148">Другой подход участвует воспроизведение циклическое стерео окружением в сочетании с пространственных звуковой отправители вокруг сцены, воспроизведение звуков одноразовые, которые выбираются в случайном порядке с точки зрения частоты тома "," шаг "и" триггера.</span><span class="sxs-lookup"><span data-stu-id="66ae8-148">A different approach involved playing a looping stereo ambience in conjunction with spatial sound emitters placed around the scene playing one-off sounds that are randomized in terms of volume, pitch and trigger frequency.</span></span> <span data-ttu-id="66ae8-149">При этом создается окружение с расширенной смысле направленность.</span><span class="sxs-lookup"><span data-stu-id="66ae8-149">This creates an ambience with an enhanced sense of directionality.</span></span> <span data-ttu-id="66ae8-150">Например, в Aguas Calientes можно слушать как каждого квадранте панорамы имеет определенные отправители, намеренно выделить определенные области geography, но работают вместе, чтобы создать общий иммерсивное окружение.</span><span class="sxs-lookup"><span data-stu-id="66ae8-150">In Aguas Calientes, for example, you can listen to how each quadrant of the panorama has specific emitters that intentionally highlight specific areas of the geography, but work together to create an overall immersive ambience.</span></span>

## <a name="tips-and-tricks"></a><span data-ttu-id="66ae8-151">Советы и рекомендации</span><span class="sxs-lookup"><span data-stu-id="66ae8-151">Tips and tricks</span></span>

<span data-ttu-id="66ae8-152">Когда вы будете помещать вместе аудио для сцены, существуют некоторые дополнительные методы, которые можно использовать для дальнейшего выделения направленность и общения, интенсивно использовать Пространственные звуковые возможности HoloLens.</span><span class="sxs-lookup"><span data-stu-id="66ae8-152">When you're putting together audio for a scene, there are some additional methods you can use to further highlight directionality and immersion, making full use of the spatial sound capabilities of HoloLens.</span></span> <span data-ttu-id="66ae8-153">Мы предоставляем список некоторых ниже — прослушивания их при следующей попытке HoloTour.</span><span class="sxs-lookup"><span data-stu-id="66ae8-153">We've provided a list of some below—listen for them the next time you try HoloTour.</span></span>
* <span data-ttu-id="66ae8-154">**Найдите целевых объектов**: Это звуки, которые активируют, только если вы работаете в отдельный объект или области рамки holographic.</span><span class="sxs-lookup"><span data-stu-id="66ae8-154">**Look Targets**: These are sounds that trigger only when you are looking at a specific object or area of the holographic frame.</span></span> <span data-ttu-id="66ae8-155">Например поиск в направлении кафе стороне улицы в Navona Piazza рим может привести к некоторой будет активировать звуки занят ресторана.</span><span class="sxs-lookup"><span data-stu-id="66ae8-155">For example, looking in the direction of the street-side café in Rome's Piazza Navona will subtly trigger the sounds of a busy restaurant.</span></span>
* <span data-ttu-id="66ae8-156">**Локальный концепции**: Путешествие хотя HoloTour содержит определенные beats, где руководство обзора, пересылке данных по голограммы, будут рассмотрены подробные раздела.</span><span class="sxs-lookup"><span data-stu-id="66ae8-156">**Local Vision**: The journey though HoloTour contains certain beats where your tour guide, aided by holograms, will explore a topic in-depth.</span></span> <span data-ttu-id="66ae8-157">К примеру как фасад Pantheon растворяющееся для отображения oculus, reverberating аудио расположить 3D передатчика с внутренней стороны Pantheon побуждает пользователя для просмотра внутренних модели.</span><span class="sxs-lookup"><span data-stu-id="66ae8-157">For instance, as the façade of the Pantheon dissolves to reveal the oculus, reverberating audio placed as a 3D emitter from the inside of the Pantheon encourages the user to explore the interior model.</span></span>
* <span data-ttu-id="66ae8-158">**Расширенный направленность**: В многих сцен мы разместили звуков в различных способов добавления наследуют параметры направления.</span><span class="sxs-lookup"><span data-stu-id="66ae8-158">**Enhanced directionality**: Within many scenes, we placed sounds in various ways to add to the directionality.</span></span> <span data-ttu-id="66ae8-159">В Pantheon сцены например, воспроизведение звука секрет был помещен как отдельные передатчика достаточно близко для пользователя таким образом, чтобы они удалось получить представление о «sonic фокусировки», как они подробно процесс вокруг play пространства.</span><span class="sxs-lookup"><span data-stu-id="66ae8-159">In the Pantheon scene, for example, the sound of the fountain was placed as a separate emitter close enough to the user so that they could get a sense of ‘sonic parallax’ as they walked around the play space.</span></span> <span data-ttu-id="66ae8-160">В сцене Salinas de Maras Перу отдельные точки зрения некоторые из потоков мало были размещены как отдельные отправители для создания более подробная внешней среды, окружающие пользователя с подлинным звуки этого расположения.</span><span class="sxs-lookup"><span data-stu-id="66ae8-160">In Peru's Salinas de Maras scene, the individual perspective of some of the little streams were placed as separate emitters to build a more immersive ambient environment, surrounding the user with the authentic sounds of that location.</span></span>
* <span data-ttu-id="66ae8-161">**Передатчик сплайна**: Этот специальный пространственных звуковой отправитель перемещает в трехмерном пространстве относительно visual позицию объекта, которому он прикреплен к.</span><span class="sxs-lookup"><span data-stu-id="66ae8-161">**Spline emitter**: This special spatial sound emitter moves in 3D space relative to the visual position of the object it's attached to.</span></span> <span data-ttu-id="66ae8-162">Примером этого было обучения в Picchu Machu, где мы использовали передатчика сплайна для предоставления уникальных представления направленность и перемещения.</span><span class="sxs-lookup"><span data-stu-id="66ae8-162">An example of this was the train in Machu Picchu, where we used a spline emitter to give a distinct sense of directionality and movement.</span></span>
* <span data-ttu-id="66ae8-163">**Музыка и SFX**: Определенные аспекты HoloTour, представляющие более стилизованные или возможности подход использовать музыкальные и звуковые эффекты для улучшения эмоциональную влияние.</span><span class="sxs-lookup"><span data-stu-id="66ae8-163">**Music and SFX**: Certain aspects of HoloTour that represent a more stylized or cinematic approach use music and sound effects to heighten the emotional impact.</span></span> <span data-ttu-id="66ae8-164">В gladiator дела в конце демонстрации рим специальные эффекты, например whooshes или stingers использовались усилению последствия меток в сценах.</span><span class="sxs-lookup"><span data-stu-id="66ae8-164">In the gladiator battle at the end of the Rome tour, special effects like whooshes or stingers were used to help strengthen the effect of labels appearing in scenes.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="66ae8-165">Об авторе</span><span class="sxs-lookup"><span data-stu-id="66ae8-165">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><span data-ttu-id="66ae8-166"><b>Джейсон Syltebo</b></span><span class="sxs-lookup"><span data-stu-id="66ae8-166"><b>Jason Syltebo</b></span></span><br><span data-ttu-id="66ae8-167">Конструктор аудио @Microsoft</span><span class="sxs-lookup"><span data-stu-id="66ae8-167">Audio Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="66ae8-168">См. также</span><span class="sxs-lookup"><span data-stu-id="66ae8-168">See also</span></span>
* [<span data-ttu-id="66ae8-169">Пространственные звука</span><span class="sxs-lookup"><span data-stu-id="66ae8-169">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="66ae8-170">Пространственные систему</span><span class="sxs-lookup"><span data-stu-id="66ae8-170">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="66ae8-171">Пространственные звук в Unity</span><span class="sxs-lookup"><span data-stu-id="66ae8-171">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="66ae8-172">Г-н пространственных 220</span><span class="sxs-lookup"><span data-stu-id="66ae8-172">MR Spatial 220</span></span>](holograms-220.md)
* [<span data-ttu-id="66ae8-173">Видео: Microsoft HoloLens: HoloTour</span><span class="sxs-lookup"><span data-stu-id="66ae8-173">Video: Microsoft HoloLens: HoloTour</span></span>](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 