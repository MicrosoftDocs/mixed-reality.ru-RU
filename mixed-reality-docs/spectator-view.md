---
title: Spectator View
description: Визуализируйте голограммы с внешнего устройства для демонстрации возможностей смешанной реальности на внешнем дисплее или записи видео о среде смешанной реальности.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, камера, ARKit, HoloLens, смешанная реальность, MixedRealityToolkit, демонстрация, запись
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491159"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="3e1cb-104">Spectator View для HoloLens и HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3e1cb-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="3e1cb-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="3e1cb-106">Overview</span></span>

<span data-ttu-id="3e1cb-107">Нося гарнитуру HoloLens, мы часто забываем, что человек, у которого ее нет, не может испытать те же удивительные возможности, что и мы.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="3e1cb-108">Spectator View позволяет другим пользователям увидеть на двухмерном экране то, что видит пользователь HoloLens в своем мире.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="3e1cb-109">Spectator View позволяет быстро и доступно записывать голограммы в формате HD на мобильных устройствах.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="3e1cb-110">Кроме того, это решение обеспечивает качественную запись голограмм видеокамерами.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="3e1cb-111">Основные ресурсы</span><span class="sxs-lookup"><span data-stu-id="3e1cb-111">Key Resources</span></span>

* [<span data-ttu-id="3e1cb-112">**Spectator View на сайте GitHub**</span><span class="sxs-lookup"><span data-stu-id="3e1cb-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="3e1cb-113">**Документация по Spectator View**</span><span class="sxs-lookup"><span data-stu-id="3e1cb-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="3e1cb-114">**Примеры для Spectator View**</span><span class="sxs-lookup"><span data-stu-id="3e1cb-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="3e1cb-115">Варианты использования</span><span class="sxs-lookup"><span data-stu-id="3e1cb-115">Use Cases</span></span>
* <span data-ttu-id="3e1cb-116">Вы можете записать взаимодействие со смешанной реальностью с помощью устройства iPhone или Android.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="3e1cb-117">Записывайте видео в формате Full HD, а также применяйте к голограммам сглаживание и даже тени.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="3e1cb-118">Это экономичный и быстрый способ записи видео голограмм.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="3e1cb-119">Передавайте видеопоток среды смешанной реальности в Apple TV непосредственно с устройства iPhone или iPad без каких-либо задержек!</span><span class="sxs-lookup"><span data-stu-id="3e1cb-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="3e1cb-120">Покажите возможности работы гостям: позвольте пользователям без HoloLens увидеть, как можно взаимодействовать с голограммами, непосредственно на телефоне или планшете.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="3e1cb-121">Текущие возможности</span><span class="sxs-lookup"><span data-stu-id="3e1cb-121">Current Features</span></span>

* <span data-ttu-id="3e1cb-122">Пространственная синхронизация голограмм позволяет всем пользователям видеть голограммы на одном и том же месте.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="3e1cb-123">Поддержка iOS (устройства с поддержкой ARKit) и Android (устройства с поддержкой ARCore).</span><span class="sxs-lookup"><span data-stu-id="3e1cb-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="3e1cb-124">Несколько гостей iOS.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-124">Multiple iOS guests.</span></span>
<span data-ttu-id="3e1cb-125">Запись видео, голограмм, окружающего звука и звука голограмм.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="3e1cb-126">Опубликуйте лист, чтобы сохранить видео, и отправьте его по электронной почте или с помощью других вспомогательных приложений.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="3e1cb-127">![Маркер](images/SpecViewPhoneDemo.jpg)
![Маркер](images/hololensspectatorview-500px.jpg) ![Маркер](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="3e1cb-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="3e1cb-128">В следующей таблице описаны различные функции Spectator View и их возможности.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="3e1cb-129">Выберите вариант, который лучше всего соответствует вашим требованиям к записи видео.</span><span class="sxs-lookup"><span data-stu-id="3e1cb-129">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="3e1cb-130">Мобильный</span><span class="sxs-lookup"><span data-stu-id="3e1cb-130">Mobile</span></span>                  |                    <span data-ttu-id="3e1cb-131">Видеокамера</span><span class="sxs-lookup"><span data-stu-id="3e1cb-131">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="3e1cb-132">Качество HD</span><span class="sxs-lookup"><span data-stu-id="3e1cb-132">HD quality</span></span>                           |         <span data-ttu-id="3e1cb-133">Full HD</span><span class="sxs-lookup"><span data-stu-id="3e1cb-133">Full HD</span></span>         |        <span data-ttu-id="3e1cb-134">Профессиональная съемка (определяется видеокамерой)</span><span class="sxs-lookup"><span data-stu-id="3e1cb-134">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="3e1cb-135">Простое перемещение камеры</span><span class="sxs-lookup"><span data-stu-id="3e1cb-135">Easy camera movement</span></span>                 |            <span data-ttu-id="3e1cb-136">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-136">✔</span></span>            |                      <span data-ttu-id="3e1cb-137">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-137">✔</span></span>                      |
| <span data-ttu-id="3e1cb-138">Вид от третьего лица</span><span class="sxs-lookup"><span data-stu-id="3e1cb-138">Third-person view</span></span>                    |            <span data-ttu-id="3e1cb-139">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-139">✔</span></span>            |                      <span data-ttu-id="3e1cb-140">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-140">✔</span></span>                      |
| <span data-ttu-id="3e1cb-141">Возможность потоковой передачи на экраны</span><span class="sxs-lookup"><span data-stu-id="3e1cb-141">Can be streamed to screens</span></span>           |            <span data-ttu-id="3e1cb-142">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-142">✔</span></span>            |                      <span data-ttu-id="3e1cb-143">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-143">✔</span></span>                      |
| <span data-ttu-id="3e1cb-144">Переносная</span><span class="sxs-lookup"><span data-stu-id="3e1cb-144">Portable</span></span>                             |            <span data-ttu-id="3e1cb-145">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-145">✔</span></span>            |                                             |
| <span data-ttu-id="3e1cb-146">Беспроводная связь</span><span class="sxs-lookup"><span data-stu-id="3e1cb-146">Wireless</span></span>                             |            <span data-ttu-id="3e1cb-147">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-147">✔</span></span>            |                                             |
| <span data-ttu-id="3e1cb-148">Дополнительное обязательное оборудование</span><span class="sxs-lookup"><span data-stu-id="3e1cb-148">Additional required hardware</span></span>         |     <span data-ttu-id="3e1cb-149">Телефон Android, iPhone</span><span class="sxs-lookup"><span data-stu-id="3e1cb-149">Android phone, iPhone</span></span>    | <span data-ttu-id="3e1cb-150">HoloLens, обвес, штатив, видеокамера, компьютер и Unity</span><span class="sxs-lookup"><span data-stu-id="3e1cb-150">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="3e1cb-151">Вложения в оборудование</span><span class="sxs-lookup"><span data-stu-id="3e1cb-151">Hardware investment</span></span>                  |           <span data-ttu-id="3e1cb-152">Низкий</span><span class="sxs-lookup"><span data-stu-id="3e1cb-152">Low</span></span>            |                     <span data-ttu-id="3e1cb-153">Высокий</span><span class="sxs-lookup"><span data-stu-id="3e1cb-153">High</span></span>                    |
| <span data-ttu-id="3e1cb-154">Поддержка разных платформ</span><span class="sxs-lookup"><span data-stu-id="3e1cb-154">Cross-platform</span></span>                       |           <span data-ttu-id="3e1cb-155">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="3e1cb-155">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="3e1cb-156">Синхронизированное содержимое</span><span class="sxs-lookup"><span data-stu-id="3e1cb-156">Synchronized content</span></span>                 |            <span data-ttu-id="3e1cb-157">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-157">✔</span></span>            |                      <span data-ttu-id="3e1cb-158">✔</span><span class="sxs-lookup"><span data-stu-id="3e1cb-158">✔</span></span>                      |
| <span data-ttu-id="3e1cb-159">Длительность настройки во время выполнения</span><span class="sxs-lookup"><span data-stu-id="3e1cb-159">Runtime setup duration</span></span>               |         <span data-ttu-id="3e1cb-160">Мгновенно</span><span class="sxs-lookup"><span data-stu-id="3e1cb-160">Instant</span></span>          |                     <span data-ttu-id="3e1cb-161">Медленно</span><span class="sxs-lookup"><span data-stu-id="3e1cb-161">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="3e1cb-162">См. также статью</span><span class="sxs-lookup"><span data-stu-id="3e1cb-162">See also</span></span>

* [<span data-ttu-id="3e1cb-163">Съемка смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="3e1cb-163">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="3e1cb-164">Съемка смешанной реальности для разработчиков</span><span class="sxs-lookup"><span data-stu-id="3e1cb-164">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="3e1cb-165">Общий доступ в смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="3e1cb-165">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
