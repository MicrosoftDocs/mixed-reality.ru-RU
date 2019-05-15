---
title: Соображения, касающиеся среды для HoloLens
description: Получите наилучшее воспроизведение с помощью HoloLens при оптимизации устройства для глаза и среды. Множества различных факторов окружающей среды совмещенного друг с другом для включения отслеживания, но разработчик смешанной реальности, существует несколько факторов можно следует учитывать объем для повышения голограммы.
author: dorreneb
ms.author: dobrown
ms.date: 04/22/2019
ms.topic: article
keywords: holographic кадра, поле зрения, fov, калибровки, пробелы, в среде, Практическое руководство
ms.openlocfilehash: 0070455792e09cd59741362b201ca6b7b9af0aec
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670172"
---
# <a name="environment-considerations-for-hololens"></a><span data-ttu-id="ebe7c-105">Соображения, касающиеся среды для HoloLens</span><span class="sxs-lookup"><span data-stu-id="ebe7c-105">Environment considerations for HoloLens</span></span>

<span data-ttu-id="ebe7c-106">HoloLens объединяет holographic со всем миром «настоящих», поместив голограммы в обстановке.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-106">HoloLens blends the holographic with the "real" world, placing holograms in your surroundings.</span></span> <span data-ttu-id="ebe7c-107">Окно приложения holographic «зависает» на стене, holographic ballerina вращается на двигалось, bunny уши располагаются поверх всего лишь нечаянная друга head.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-107">A holographic app window "hangs" on the wall, a holographic ballerina spins on the tabletop, bunny ears sit on top of your unwitting friend’s head.</span></span> <span data-ttu-id="ebe7c-108">При использовании иммерсивных игр или приложений, holographic мира будет распространяться для заполнения обстановке — но вы по-прежнему сможете см. в разделе и перемещать пространство.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-108">When you’re using an immersive game or app, the holographic world will spread to fill your surroundings —but you’ll still be able to see and move around the space.</span></span>

<span data-ttu-id="ebe7c-109">Голограммы, что вы помещаете останется где вы помещаете их туда, даже при отключении устройства.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-109">The holograms you place will stay where you’ve put them, even if you turn off your device.</span></span> 

## <a name="setting-up-an-environment"></a><span data-ttu-id="ebe7c-110">Настройка среды</span><span class="sxs-lookup"><span data-stu-id="ebe7c-110">Setting up an environment</span></span>

<span data-ttu-id="ebe7c-111">Устройства HoloLens научитесь размещать стабильными и точные голограммы по *отслеживания* пользователей в пространстве.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-111">HoloLens devices know how to place stable and accurate holograms by *tracking* users in a space.</span></span> <span data-ttu-id="ebe7c-112">Без правильного отслеживания устройства не понимает среды или пользователя в ней — поэтому голограммы может отображаться в неправильных местах, не отображаются в одно место каждый раз или вообще не отображается.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-112">Without proper tracking, the device does not understand the environment or the user within it - so holograms can appear in the wrong places, not appear in the same spot every time, or not appear at all.</span></span>

<span data-ttu-id="ebe7c-113">Отслеживание производительности сильно зависят от среды, в которой находится пользователь и помощник по настройке среды, чтобы вызвать стабильное и согласованное отслеживания является искусством, а не наукой.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-113">Tracking performance is heavily influenced by the environment the user is in, and tuning an environment to induce stable and consistent tracking is an art rather than a science.</span></span> <span data-ttu-id="ebe7c-114">Множества различных факторов окружающей среды совмещенного друг с другом для включения отслеживания, но разработчик смешанной реальности, существует несколько факторов можно следует учитывать объем для более точного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-114">Many different environmental factors are fused together to enable tracking, but as a Mixed Reality developer, there are several factors you can keep in mind to tune a space for better tracking.</span></span>
 
### <a name="lighting"></a><span data-ttu-id="ebe7c-115">Освещение</span><span class="sxs-lookup"><span data-stu-id="ebe7c-115">Lighting</span></span>
<span data-ttu-id="ebe7c-116">Смешанная реальность Windows использует светлой визуальной для отслеживания из местоположения пользователя.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-116">Windows Mixed Reality uses visual light to track the user's location.</span></span> <span data-ttu-id="ebe7c-117">Если окружение находится слишком ярким, камеры можно получить пропускная способность, и ничего не отображается.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-117">When an environment is too bright, the cameras can get saturated, and nothing is seen.</span></span> <span data-ttu-id="ebe7c-118">Если среда является слишком темно-, камеры не может взять достаточно информации, и ничего не отображается.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-118">If the environment is too dark, the cameras cannot pick up enough information, and nothing is seen.</span></span> <span data-ttu-id="ebe7c-119">Освещение следует еще и достаточно ярко, человек видно без усилий, но не так яркость неудобно, света, для просмотра.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-119">Lighting should be even and sufficiently bright that a human can see without effort, but not so bright that the light is painful to look at.</span></span>

<span data-ttu-id="ebe7c-120">Области которых ярко-света в целом dim области моментов также проблематично, как камеры, который необходимо настроить при перемещении в нее ярко-пробелов.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-120">Areas where there are points of bright light in an overall dim area are also problematic, as the camera has to adjust when moving in and out of bright spaces.</span></span> <span data-ttu-id="ebe7c-121">Это может привести к устройству «потерять» и думаю, что изменения в свете приравнивается к изменению расположения.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-121">This can cause the device to "get lost" and think that the change in light equates to a change in location.</span></span> <span data-ttu-id="ebe7c-122">Стабильные освещенности в области приведет к более точного отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-122">Stable light levels in an area will lead to better tracking.</span></span>

<span data-ttu-id="ebe7c-123">Любое внешнее освещение может также привести к нестабильности в инспекторе как со временем может значительно меняться Солнце.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-123">Any outdoor lighting can also cause instability in the tracker, as the sun may vary considerably over time.</span></span> <span data-ttu-id="ebe7c-124">Например отслеживания в одном пространстве летом и зимних результаты могут быть значительно различными, как secondhand света за пределами может быть более поздней версии в разное время года.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-124">For example, tracking in the same space in the summer vs. winter can produce drastically different results, as the secondhand light outside may be higher at different times of year.</span></span>

<span data-ttu-id="ebe7c-125">При наличии luxmeter постоянной lux 500 – 1000 — это хорошее начало.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-125">If you have a luxmeter, a steady 500-1000 lux is a good place to start.</span></span> 

#### <a name="types-of-lighting"></a><span data-ttu-id="ebe7c-126">Виды освещения</span><span class="sxs-lookup"><span data-stu-id="ebe7c-126">Types of lighting</span></span>
<span data-ttu-id="ebe7c-127">Различные типы света в пространстве может также повлиять на отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-127">Different types of light in a space can also influence tracking.</span></span> <span data-ttu-id="ebe7c-128">Лампочек импульсный с AC электроэнергии, под управлением через него — Если частота AC 50 Гц, то источник света импульсами 50 Гц.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-128">Lightbulbs pulse with the AC electricity running through it - if the AC frequency is 50Hz, then the light pulses at 50Hz.</span></span> <span data-ttu-id="ebe7c-129">Для пользователя этот пульсирующий является не заметил.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-129">For a human, this pulsing is not noticed.</span></span> <span data-ttu-id="ebe7c-130">Тем не менее камеры 30 кадров/с HoloLens видит эти изменения — некоторые фреймы будут хорошо освещенная, некоторые будет гореть плохо и некоторые будут чрезмерно представлены в виде камеры пытается компенсировать света импульсов.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-130">However, HoloLens' 30fps camera sees these changes - some frames will be well-lit, some will be poorly lit, and some will be over-exposed as the camera tries to compensate for light pulses.</span></span>

<span data-ttu-id="ebe7c-131">В США электроэнергии частота стандартной является 60 Гц, поэтому импульсов lightbulb используемому с частотой кадров HoloLens - align импульсов 60 Гц с частотой кадров 30 кадров/с Hololens.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-131">In the USA, electricity frequency standard is 60Hz, so lightbulb pulses are harmonized with HoloLens' framerate - 60Hz pulses align with Hololens' 30 FPS framerate.</span></span> <span data-ttu-id="ebe7c-132">Тем не менее во многих странах действуют стандартом частота переменного ТОКА от 50 Гц, это означает некоторые фреймы Hololens будут выполнены во время импульсов, а другие — нет.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-132">However, many countries have an AC frequency standard of 50Hz, which means some Hololens frames will be taken during pulses, and others will not.</span></span> <span data-ttu-id="ebe7c-133">В частности флюоресцентные освещения в Европе известно, привести к проблемам.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-133">In particular, fluorescent lighting in Europe has been known to cause issues.</span></span> 

<span data-ttu-id="ebe7c-134">Можно попытаться устранить мерцание проблемы на несколько моментов.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-134">There are a few things you can try to resolve flickering issues.</span></span> <span data-ttu-id="ebe7c-135">Температуры, возраст лампочки и циклов прогрева — распространенные причины флюоресцентные мерцание и заменив bulbs могут помочь.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-135">Temperature, bulb age, and warm-up cycles are common causes of fluorescent flickering and replacing bulbs may help.</span></span> <span data-ttu-id="ebe7c-136">Кроме того, помогает усилению bulbs и убедиться, что текущий рисует являются постоянными.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-136">Tightening bulbs and making sure current draws are constant can also help.</span></span> 

### <a name="items-in-a-space"></a><span data-ttu-id="ebe7c-137">Элементы в пространстве</span><span class="sxs-lookup"><span data-stu-id="ebe7c-137">Items in a space</span></span>
<span data-ttu-id="ebe7c-138">HoloLens использует уникальный ориентиры окружающей среды, также известный как *функции*, чтобы найти сам в пространстве.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-138">HoloLens uses unique environmental landmarks, also known as *features*, to locate itself in a space.</span></span> 

<span data-ttu-id="ebe7c-139">Устройство практически никогда не можно отслеживать в области компонентов плохо, устройство имеет нет способа узнать, где в пространстве это.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-139">A device can almost never track in a feature-poor area, as the device has no way of knowing where in space it is.</span></span> <span data-ttu-id="ebe7c-140">Добавление функций со стенами пространства обычно — хороший способ улучшить отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-140">Adding features to the walls of a space is usually a good way to improve tracking.</span></span> <span data-ttu-id="ebe7c-141">Плакаты, символы лентой на стене, растения, уникальные объекты или другие похожие элементы всех разделов справки.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-141">Posters, symbols taped to a wall, plants, unique objects, or other similar items all help.</span></span> <span data-ttu-id="ebe7c-142">Запутанным поддержки представляет собой хороший пример среды, приводит к хорошим отслеживания — существует множество различных функций в одной области.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-142">A messy desk is a good example of an environment that leads to good tracking - there are a lot of different features in a single area.</span></span> 

<span data-ttu-id="ebe7c-143">Кроме того использующих уникальные функции в одном пространстве.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-143">Additionally, use unique features in the same space.</span></span> <span data-ttu-id="ebe7c-144">Же плакат повторить несколько раз на стене, например, будет ввести в заблуждение устройства как HoloLens не будет знать, какой из повторяющихся плакаты, он просматривает.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-144">The same poster repeated multiple times over a wall, for example, will cause device confusion as the HoloLens won't know which of the repetitive posters it is looking at.</span></span> <span data-ttu-id="ebe7c-145">Один из способов добавления уникальные возможности является использование строки маски ленты, чтобы создать уникальный, шаблоны nonrepetitve вдоль стенок и основания пробел.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-145">One common way of adding unique features is to use lines of masking tape to create unique, nonrepetitve patterns along the walls and floor of a space.</span></span> 

<span data-ttu-id="ebe7c-146">Хороший вопрос, нужно задать себе такое - Если вы видели лишь небольшая часть сцены, удалось вы однозначно найти вручную в пространстве</span><span class="sxs-lookup"><span data-stu-id="ebe7c-146">A good question to ask yourself is - if you saw just a small amount of the scene, could you uniquely locate yourself in the space?</span></span> <span data-ttu-id="ebe7c-147">В противном случае вполне вероятно, могут возникнуть проблемы, а также отслеживания с устройства.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-147">If not, it's likely the device will have problems tracking as well.</span></span>

#### <a name="wormholes"></a><span data-ttu-id="ebe7c-148">Норки</span><span class="sxs-lookup"><span data-stu-id="ebe7c-148">Wormholes</span></span>
<span data-ttu-id="ebe7c-149">При наличии двух областей или областей, которые выглядят одинаково, средство отслеживания может думаю, что они совпадают.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-149">If you have two areas or regions that look the same, the tracker may think they are the same.</span></span> <span data-ttu-id="ebe7c-150">Это приводит к честных сам он считает устройство является другое место.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-150">This results in the device tricking itself into thinking it is somewhere else.</span></span> <span data-ttu-id="ebe7c-151">Мы называем эти типы из повторяющихся областей *норки*.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-151">We call these types of repetitive areas *wormholes*.</span></span> 

<span data-ttu-id="ebe7c-152">Чтобы предотвратить норки, Постарайтесь избежать идентичных областей в одном пространстве.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-152">To prevent wormholes, try to prevent identical areas in the same space.</span></span> <span data-ttu-id="ebe7c-153">Идентичные области иногда могут содержать станций фабрики, windows и модернизации зданий, серверных стойках или рабочими станциями.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-153">Identical areas can sometimes include factory stations, windows on a building, server racks, or work stations.</span></span> <span data-ttu-id="ebe7c-154">Маркировка областей или добавление уникальных функций в каждой области похожими позволяет устранить норки.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-154">Labelling areas or adding unique features to each similar-looking areas can help mitigate wormholes.</span></span>
 
### <a name="temporal-stability-of-a-space"></a><span data-ttu-id="ebe7c-155">Временные стабильность пространства</span><span class="sxs-lookup"><span data-stu-id="ebe7c-155">Temporal stability of a space</span></span>
<span data-ttu-id="ebe7c-156">Если среда постоянно сдвиг и изменение, устройство не обладает стабильной функциями для поиска от.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-156">If your environment is constantly shifting and changing, the device has no stable features to locate against.</span></span> 

<span data-ttu-id="ebe7c-157">Больше перемещаемых объекты, которые находятся в пространстве, включая людей, проще терять отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-157">The more moving objects that are in a space, including people, the easier it is to lose tracking.</span></span> <span data-ttu-id="ebe7c-158">Перемещение конвейерных лент, элементы в различных состояниях конструкции и большое число пользователей в пространстве все зоны известны вызывали проблемы отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-158">Moving conveyor belts, items in different states of construction, and lots of people in a space have all been known to cause tracking issues.</span></span>
 
### <a name="proximity-of-the-user-to-items-in-the-space"></a><span data-ttu-id="ebe7c-159">С учетом расположения пользователя к элементам в пространстве</span><span class="sxs-lookup"><span data-stu-id="ebe7c-159">Proximity of the user to items in the space</span></span>
<span data-ttu-id="ebe7c-160">Точно так же как люди не может сосредоточиться на объекты близко к глаза, HoloLens несравнимы с трудностями при объекты близкие к его камеры.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-160">Similarly to how humans cannot focus well on objects close to the eyes, HoloLens struggles when objects are close to it's cameras.</span></span> <span data-ttu-id="ebe7c-161">Если объект находится слишком близко для того, чтобы убедиться в обоих камеры или объект блокирует один камеры, устройство будет иметь гораздо больше проблем, с помощью отслеживания для объекта.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-161">If an object is too close to be seen with both cameras, or if an object is blocking one camera, the device will have far more issues with tracking against the object.</span></span> 

<span data-ttu-id="ebe7c-162">Камеры можно увидеть не ближе, чем 15cm из объекта.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-162">The cameras can see no closer than 15cm from an object.</span></span>
 
### <a name="surfaces-in-a-space"></a><span data-ttu-id="ebe7c-163">Поверхности в пространстве</span><span class="sxs-lookup"><span data-stu-id="ebe7c-163">Surfaces in a space</span></span>
<span data-ttu-id="ebe7c-164">Строго Светящийся поверхности, скорее всего будет выглядеть различается в зависимости от угол, влияющий на отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-164">Strongly reflective surfaces will likely look different depending on the angle, which affects tracking.</span></span> <span data-ttu-id="ebe7c-165">Представить новый автомобиль - при перемещении вокруг него, отражает свет и вы увидите разные объекты в рабочей области, при перемещении.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-165">Think of a brand new car - when you move around it, light reflects and you see different objects in the surface as you move.</span></span> <span data-ttu-id="ebe7c-166">Объекту отслеживания разных объектов отражаются в поверхности представляют изменяющейся среде и устройство теряет отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-166">To the tracker, the different objects reflected in the surface represent a changing environment, and the device loses tracking.</span></span>

<span data-ttu-id="ebe7c-167">Меньше Блестящий объектами работать проще для отслеживания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-167">Less shiny objects are easier to track against.</span></span>

### <a name="wifi-fingerprint-considerations"></a><span data-ttu-id="ebe7c-168">Рекомендации по отпечатку пальца Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="ebe7c-168">WiFi fingerprint considerations</span></span>
<span data-ttu-id="ebe7c-169">До тех пор, пока включен Wi-Fi, карты будет коррелировать данные с помощью отпечатка пальца Wi-Fi, даже в том случае, если не подключен к фактическое Wi-Fi сеть или маршрутизатор.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-169">As long as WiFi is enabled, map data will be correlated with a WiFi fingerprint, even when not connected to an actual WiFi network/router.</span></span> <span data-ttu-id="ebe7c-170">Без сведений о Wi-Fi места и голограммы может работать немного медленнее, для распознавания.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-170">Without WiFi info, the space and holograms may be slightly slower to recognize.</span></span> <span data-ttu-id="ebe7c-171">При существенном изменении сигналов Wi-Fi устройства может думаю, что он полностью находится в другое пространство.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-171">If the WiFi signals change significantly, the device may think it is in a different space altogether.</span></span>

<span data-ttu-id="ebe7c-172">Сетевой идентификации (т. е. SSID, MAC-адрес) не отправляются в Майкрософт и все Wi-Fi, ссылки сохраняются локального HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-172">Network identification (i.e. SSID, MAC address) is not sent to Microsoft, and all WiFi references are kept local on the HoloLens.</span></span>

## <a name="mapping-new-spaces"></a><span data-ttu-id="ebe7c-173">Новые модули сопоставления</span><span class="sxs-lookup"><span data-stu-id="ebe7c-173">Mapping new spaces</span></span>
<span data-ttu-id="ebe7c-174">При вводе нового пространства (или загрузить существующий), вы увидите график сетки, распространение через пространство.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-174">When you enter a new space (or load an existing one), you’ll see a mesh graphic spreading over the space.</span></span> <span data-ttu-id="ebe7c-175">Это означает, что устройство является [сопоставление обстановке](spatial-mapping-design.md).</span><span class="sxs-lookup"><span data-stu-id="ebe7c-175">This means your device is [mapping your surroundings](spatial-mapping-design.md).</span></span> 

<span data-ttu-id="ebe7c-176">Если возникают проблемы, поместив голограммы, попробуйте прогулке по пространство, поэтому HoloLens можно сопоставить их более подробно.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-176">If you’re having trouble placing holograms, try walking around the space so HoloLens can map it more fully.</span></span> 

<span data-ttu-id="ebe7c-177">Если ваш HoloLens невозможно сопоставить свою область или выходит за пределы калибровки, можно ввести режим Limited.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-177">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="ebe7c-178">В ограниченном режиме будет помещать голограммы в обстановке.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-178">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="environment-management"></a><span data-ttu-id="ebe7c-179">Среда управления</span><span class="sxs-lookup"><span data-stu-id="ebe7c-179">Environment management</span></span>
<span data-ttu-id="ebe7c-180">Существует два параметра, которые позволяют пользователям «Очистка» голограммы и причина HoloLens пробел «отложить».</span><span class="sxs-lookup"><span data-stu-id="ebe7c-180">There are two settings which enable users to “clean up” holograms and cause HoloLens to “forget" a space.</span></span>  <span data-ttu-id="ebe7c-181">Они существуют в «Голограммы и сред» в настройках приложения, второй параметр, также отображаются в разделе «Конфиденциальность» в настройках приложения.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-181">They exist in “Holograms and environments” in the settings app, with the second setting also appearing under “Privacy” in the settings app.</span></span>

1.  <span data-ttu-id="ebe7c-182">Удаление ближайших голограммы-Если выбрать этот параметр, HoloLens будут удалены все привязанные голограммы и всех данных хранимой карты для «текущее место», где находится устройство.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-182">Delete nearby holograms – By selecting this setting, HoloLens will erase all anchored holograms and all stored map data for the “current space” where the device is located.</span></span>  <span data-ttu-id="ebe7c-183">Новый раздел карты будет можно создавать и сохранять в базе данных для этого расположения, после голограммы снова помещаются в этой же области.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-183">A new map section would be created and stored in the database for that location once Holograms are again placed in that same space.</span></span>

2.  <span data-ttu-id="ebe7c-184">Удаление всех голограммы-, выбрав этот параметр, HoloLens, будут удалены все данные карты и привязываются голограммы в базах данных всей пробелов.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-184">Delete all holograms – By selecting this setting, HoloLens will erase ALL map data and anchored holograms in the entire databases of spaces.</span></span>  <span data-ttu-id="ebe7c-185">Нет голограммы, на которые будет найдено повторно, и любой голограммы необходимо вновь разместить снова хранить разделах карты в базе данных.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-185">No holograms will be rediscovered and any holograms need to be newly placed to again store map sections in the database.</span></span>

### <a name="managing-your-spaces"></a><span data-ttu-id="ebe7c-186">Управление вашей пробелы</span><span class="sxs-lookup"><span data-stu-id="ebe7c-186">Managing your spaces</span></span>

<span data-ttu-id="ebe7c-187">Разделы карты и разные пространства свернуты в отдельной базы данных, хранящихся локально на устройство HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-187">The map sections and different spaces have been collapsed into a single database, stored locally on the HoloLens device.</span></span> <span data-ttu-id="ebe7c-188">Базе данных сопоставления надежно сохранены, доступ, доступны только для внутренней системы и никогда не для пользователя устройства, даже в том случае, если подключено к Компьютеру и/или с помощью обозревателя файлов приложения.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-188">The map database is stored securely, with access only available to the internal system, and never to a user of the device, even when plugged into a PC and/or using the file explorer app.</span></span> <span data-ttu-id="ebe7c-189">При включении bitlocker, данные хранимых карты также шифруются.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-189">When bitlocker is enabled, the stored map data is also encrypted.</span></span>

<span data-ttu-id="ebe7c-190">При голограммы размещаются в разных местах без соединительных пути между расположения/голограммы существуют несколько компонентов карты.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-190">Multiple map components exist when holograms are placed in different locations without a connective path between the locations/holograms.</span></span>  <span data-ttu-id="ebe7c-191">Закреплено в том же разделе карты голограммы считаются «рядом» в текущем пространстве.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-191">Holograms anchored within the same map section are considered to be “nearby” in the current space.</span></span>

<span data-ttu-id="ebe7c-192">Есть API для экспорта небольшой набор «текущее пространство» для разработчиков (часть карты компонент, который в данный момент распознается) для реализации общей голограмма сценариев.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-192">There is a developer API to export a small subset of the “current space” (a portion the map component that is currently recognized) to enable shared hologram scenarios.</span></span>  <span data-ttu-id="ebe7c-193">В настоящее время отсутствует механизм для загрузки всех областей, которые были сопоставлены всей базы данных.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-193">There is currently no mechanism to download the entire database of all spaces that have been mapped.</span></span>


## <a name="hologram-quality"></a><span data-ttu-id="ebe7c-194">Голограмма качества</span><span class="sxs-lookup"><span data-stu-id="ebe7c-194">Hologram quality</span></span>

<span data-ttu-id="ebe7c-195">Голограммы могут быть помещены в производственной среде — высокой, низкой и по всему вы — но вы увидите их [holographic кадра](holographic-frame.md) , который выступает посредником перед глазами пользователя.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-195">Holograms can be placed throughout your environment—high, low, and all around you—but you’ll see them through a [holographic frame](holographic-frame.md) that sits in front of your eyes.</span></span> <span data-ttu-id="ebe7c-196">Для получения лучшего представления, не забудьте настроить устройства, чтобы можно было видеть весь кадр.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-196">To get the best view, make sure to adjust your device so you can see the entire frame.</span></span> <span data-ttu-id="ebe7c-197">И обращайтесь к сильна среды и изучение!</span><span class="sxs-lookup"><span data-stu-id="ebe7c-197">And don’t hesitate to walk around your environment and explore!</span></span>

<span data-ttu-id="ebe7c-198">Для вашего [голограммы](hologram.md) поиск четкое, понятным и стабильной, ваш HoloLens необходимо можно уточнять только для вас.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-198">For your [holograms](hologram.md) to look crisp, clear, and stable, your HoloLens needs to be calibrated just for you.</span></span> <span data-ttu-id="ebe7c-199">При первой настройке вашего HoloLens, вы получите пошаговые этот процесс.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-199">When you first set up your HoloLens, you’ll be guided through this process.</span></span> <span data-ttu-id="ebe7c-200">Далее Если голограммы отображаются неправильно или вы видите большое число ошибок, можно внести изменения.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-200">Later on, if holograms don’t look right or you’re seeing a lot of errors, you can make adjustments.</span></span>

### <a name="calibration"></a><span data-ttu-id="ebe7c-201">Калибровки</span><span class="sxs-lookup"><span data-stu-id="ebe7c-201">Calibration</span></span>

<span data-ttu-id="ebe7c-202">Если ваш голограммы перебои управления или "дрожащее" изображение, или если возникают проблемы, поместив голограммы, в первую очередь необходимо попробовать [калибровки приложения](calibration.md).</span><span class="sxs-lookup"><span data-stu-id="ebe7c-202">If your holograms look jittery or shaky, or if you’re having trouble placing holograms, the first thing to try is the [Calibration app](calibration.md).</span></span> <span data-ttu-id="ebe7c-203">Это приложение также может помочь при возникновении любой discomfort при использовании вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-203">This app can also help if you’re experiencing any discomfort while using your HoloLens.</span></span>

<span data-ttu-id="ebe7c-204">Чтобы открыть приложение калибровки, перейдите к параметрам > Система > Служебные программы.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-204">To get to the Calibration app, go to Settings > System > Utilities.</span></span> <span data-ttu-id="ebe7c-205">Выберите открыть калибровки и следуйте инструкциям.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-205">Select Open Calibration and follow the instructions.</span></span>

<span data-ttu-id="ebe7c-206">Если вы запустите приложение калибровки и по-прежнему возникают проблемы с качеством голограмма, или вы видите часто сообщение «отслеживание потеряны», попробуйте приложение настройке датчика.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-206">If you run the Calibration app and are still having problems with hologram quality, or you’re seeing a frequent “tracking lost” message, try the Sensor Tuning app.</span></span> <span data-ttu-id="ebe7c-207">Выберите Settings > Система > Служебные программы, выберите открыть настройку датчиков и следуйте инструкциям.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-207">Go to Settings > System > Utilities, select Open Sensor Tuning, and follow the instructions.</span></span>

<span data-ttu-id="ebe7c-208">Если кто-то другой будет использоваться ваш HoloLens, их следует запустить приложение калибровки во-первых, устройство настроено правильно для них.</span><span class="sxs-lookup"><span data-stu-id="ebe7c-208">If someone else is going to be using your HoloLens, they should run the Calibration app first so the device is set up properly for them.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebe7c-209">См. также</span><span class="sxs-lookup"><span data-stu-id="ebe7c-209">See also</span></span>
* [<span data-ttu-id="ebe7c-210">Проектирование пространственного сопоставления</span><span class="sxs-lookup"><span data-stu-id="ebe7c-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="ebe7c-211">Голограммы</span><span class="sxs-lookup"><span data-stu-id="ebe7c-211">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="ebe7c-212">Калибровка</span><span class="sxs-lookup"><span data-stu-id="ebe7c-212">Calibration</span></span>](calibration.md)