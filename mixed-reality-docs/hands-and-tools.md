---
title: Руки и контроллеры движения
description: Обзор взаимодействия между движениями и контроллерами движений
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Смешанная реальность, руки, управляемые движения, взаимодействие, проектирование
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039169"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="adb00-104">Руки и контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="adb00-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="adb00-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="adb00-105">Scenarios</span></span>
<span data-ttu-id="adb00-106">Если вы решили применить эту модель взаимодействия после ознакомления с [рекомендациями](interaction-fundamentals.md)по проектированию, это означает, что вы разрабатываете приложение, которое требует от пользователей использовать две руки для взаимодействия с Holographic.</span><span class="sxs-lookup"><span data-stu-id="adb00-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="adb00-107">В приложении будет достигнута цель удаления границ между виртуальными и физическими.</span><span class="sxs-lookup"><span data-stu-id="adb00-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="adb00-108">Некоторые конкретные сценарии могут быть:</span><span class="sxs-lookup"><span data-stu-id="adb00-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="adb00-109">Предоставление информационным работникам 2D виртуальный экранов и интерфейсов пользователя для просмотра и управления содержимым</span><span class="sxs-lookup"><span data-stu-id="adb00-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="adb00-110">Руководства и руководства для сотрудников первой строки в заводской сборке</span><span class="sxs-lookup"><span data-stu-id="adb00-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="adb00-111">Разработка профессиональных средств для помощи и обучения медицинских специалистов</span><span class="sxs-lookup"><span data-stu-id="adb00-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="adb00-112">Использование трехмерных виртуальных объектов для украшения реального мира или для создания второго мира</span><span class="sxs-lookup"><span data-stu-id="adb00-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="adb00-113">Создание служб и игр на основе расположения в качестве фона в реальном мире</span><span class="sxs-lookup"><span data-stu-id="adb00-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="adb00-114">Руки и контроллеры движения модальностей</span><span class="sxs-lookup"><span data-stu-id="adb00-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="adb00-115">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="adb00-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="adb00-116">Это модальность, использующая возможности руки, с помощью которых пользователи могут касаться голограмм и манипулировать ими напрямую.</span><span class="sxs-lookup"><span data-stu-id="adb00-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="adb00-117">Леаверагинг ежедневные работы и предоставляя верные визуальные аффорданцес, пользователи могут использовать тот же способ управления реальными объектами для взаимодействия с виртуальными.</span><span class="sxs-lookup"><span data-stu-id="adb00-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="adb00-118">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="adb00-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="adb00-119">Такое модальность позволяет пользователям взаимодействовать с голограммами на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="adb00-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="adb00-120">Он позволяет пользователям лучше использовать окружающую подстановку.</span><span class="sxs-lookup"><span data-stu-id="adb00-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="adb00-121">Пользователи могут размещать голограммы в любом месте и по-прежнему обращаться к ним с любых расстояний.</span><span class="sxs-lookup"><span data-stu-id="adb00-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="adb00-122">Модели и жесты, используемые для управления и манипулирования плоскими и трехмерными голограммами, высоко синхронизированы с этими моделями с прямой манипуляцией.</span><span class="sxs-lookup"><span data-stu-id="adb00-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="adb00-123">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="adb00-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="adb00-124">Контроллеры движения — это средства, расширяющие физические возможности пользователей путем предоставления точных взаимодействий между большим диапазоном расстояний при использовании одной или обеих стрелок.</span><span class="sxs-lookup"><span data-stu-id="adb00-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="adb00-125">Эти аксессуары оборудования предоставляют ярлыки для многих часто используемых взаимодействий и дают сурефутед, тактиле Отзывы о различных действиях.</span><span class="sxs-lookup"><span data-stu-id="adb00-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="adb00-126">В настоящее время контроллеры движения доступны только для сценариев ВМР.</span><span class="sxs-lookup"><span data-stu-id="adb00-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="adb00-127">См. также</span><span class="sxs-lookup"><span data-stu-id="adb00-127">See also</span></span>
* [<span data-ttu-id="adb00-128">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="adb00-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="adb00-129">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="adb00-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="adb00-130">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="adb00-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="adb00-131">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="adb00-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="adb00-132">Режимы без использования рук</span><span class="sxs-lookup"><span data-stu-id="adb00-132">Hands-free</span></span>](hands-free.md)
