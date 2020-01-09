---
title: Руки и контроллеры движения
description: Обзор взаимодействия между движениями и контроллерами движений
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Смешанная реальность, руки, контроллеры движения, взаимодействие, проектирование
ms.openlocfilehash: 27d13316bbc4b3b40a1e617d73dd5487c05cb347
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334446"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="3e0b8-104">Руки и контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="3e0b8-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="3e0b8-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="3e0b8-105">Scenarios</span></span>
<span data-ttu-id="3e0b8-106">Если вы решили применить эту модель взаимодействия после считывания [обзора взаимодействия](interaction-fundamentals.md), это означает, что вы разрабатываете приложение, которое требует от пользователей использовать две руки для взаимодействия с Holographic.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="3e0b8-107">В приложении будет достигнута цель удаления границы между виртуальными и физическими.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="3e0b8-108">Некоторые конкретные сценарии могут быть:</span><span class="sxs-lookup"><span data-stu-id="3e0b8-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="3e0b8-109">Предоставление информационных работников 2D виртуальных экранов с аффорданцес пользовательского интерфейса для просмотра и управления содержимым</span><span class="sxs-lookup"><span data-stu-id="3e0b8-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="3e0b8-110">Руководства и руководства для сотрудников первой строки для заводской сборки</span><span class="sxs-lookup"><span data-stu-id="3e0b8-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="3e0b8-111">Разработка профессиональных средств для помощи и обучения медицинских специалистов</span><span class="sxs-lookup"><span data-stu-id="3e0b8-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="3e0b8-112">Использование трехмерных виртуальных объектов для украшения реального мира или для создания второго мира</span><span class="sxs-lookup"><span data-stu-id="3e0b8-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="3e0b8-113">Создание служб и игр на основе местоположения с использованием реального мира в качестве фона</span><span class="sxs-lookup"><span data-stu-id="3e0b8-113">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="3e0b8-114">Руки и контроллеры движения модальностей</span><span class="sxs-lookup"><span data-stu-id="3e0b8-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="3e0b8-115">[![прямой манипуляции с помощью руки](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="3e0b8-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsdirect-manipulationmdbr"></a>[<span data-ttu-id="3e0b8-116">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="3e0b8-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="3e0b8-117">Это модальность, использующая возможности руки, с помощью которых пользователи могут касаться голограмм и манипулировать ими напрямую.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="3e0b8-118">Используя ежедневные возможности и предоставляя верные визуальные аффорданцес, пользователи могут использовать тот же способ управления реальными объектами для взаимодействия с виртуальными.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3e0b8-119">[![точки и фиксация с помощью руки](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="3e0b8-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handspoint-and-commitmdbr"></a>[<span data-ttu-id="3e0b8-120">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="3e0b8-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="3e0b8-121">Такое модальность позволяет пользователям взаимодействовать с голограммами на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="3e0b8-122">Он позволяет пользователям лучше использовать окружающую подстановку.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="3e0b8-123">Пользователи могут размещать голограммы в любом месте и по-прежнему обращаться к ним с любого расстояния.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-123">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="3e0b8-124">Модели и жесты, используемые для управления и манипулирования плоскими и трехмерными голограммами, высоко синхронизированы с этими моделями с прямой манипуляцией.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3e0b8-125">[![контроллеры движения](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="3e0b8-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersmotion-controllersmdbr"></a>[<span data-ttu-id="3e0b8-126">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="3e0b8-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="3e0b8-127">Контроллеры движения — это средства, расширяющие физические возможности пользователя путем предоставления точных взаимодействий между большим диапазоном расстояний при использовании одной или обеих стрелок.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="3e0b8-128">Эти аксессуары оборудования предоставляют ярлыки для многих часто используемых взаимодействий и предоставляют сурефутед, тактиле Отзывы о различных действиях.</span><span class="sxs-lookup"><span data-stu-id="3e0b8-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="3e0b8-129">В настоящее время контроллеры движения доступны только для сценариев Windows Mixed Reality (ВМР).</span><span class="sxs-lookup"><span data-stu-id="3e0b8-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="3e0b8-130">См. также статью</span><span class="sxs-lookup"><span data-stu-id="3e0b8-130">See also</span></span>
* [<span data-ttu-id="3e0b8-131">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="3e0b8-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="3e0b8-132">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="3e0b8-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="3e0b8-133">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="3e0b8-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3e0b8-134">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="3e0b8-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="3e0b8-135">Режимы без использования рук</span><span class="sxs-lookup"><span data-stu-id="3e0b8-135">Hands-free</span></span>](hands-free.md)
