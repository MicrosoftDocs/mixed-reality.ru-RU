---
title: Руки и контроллеры движения
description: Обзор взаимодействия между движениями и контроллерами движений
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Смешанная реальность, руки, управляемые движения, взаимодействие, проектирование
ms.openlocfilehash: b6efb0a9651cad8eee9b80bb130aa1a85b9a9941
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507871"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="cf58d-104">Руки и контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="cf58d-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="cf58d-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="cf58d-105">Scenarios</span></span>
<span data-ttu-id="cf58d-106">Если вы решили применить эту модель взаимодействия после ознакомления с [рекомендациями](interaction-fundamentals.md)по проектированию, это означает, что вы разрабатываете приложение, которое требует от пользователей использовать две руки для взаимодействия с Holographic.</span><span class="sxs-lookup"><span data-stu-id="cf58d-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="cf58d-107">В приложении будет достигнута цель удаления границ между виртуальными и физическими.</span><span class="sxs-lookup"><span data-stu-id="cf58d-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="cf58d-108">Некоторые конкретные сценарии могут быть:</span><span class="sxs-lookup"><span data-stu-id="cf58d-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="cf58d-109">Предоставление информационным работникам 2D виртуальный экранов и интерфейсов пользователя для просмотра и управления содержимым</span><span class="sxs-lookup"><span data-stu-id="cf58d-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="cf58d-110">Руководства и руководства для сотрудников первой строки в заводской сборке</span><span class="sxs-lookup"><span data-stu-id="cf58d-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="cf58d-111">Разработка профессиональных средств для помощи и обучения медицинских специалистов</span><span class="sxs-lookup"><span data-stu-id="cf58d-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="cf58d-112">Использование трехмерных виртуальных объектов для украшения реального мира или для создания второго мира</span><span class="sxs-lookup"><span data-stu-id="cf58d-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="cf58d-113">Создание служб и игр на основе расположения в качестве фона в реальном мире</span><span class="sxs-lookup"><span data-stu-id="cf58d-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="cf58d-114">Руки и контроллеры движения модальностей</span><span class="sxs-lookup"><span data-stu-id="cf58d-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="cf58d-115">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="cf58d-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="cf58d-116">Это модальность, использующая возможности руки, с помощью которых пользователи могут касаться голограмм и манипулировать ими напрямую.</span><span class="sxs-lookup"><span data-stu-id="cf58d-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="cf58d-117">Леаверагинг ежедневные работы и предоставляя верные визуальные аффорданцес, пользователи могут использовать тот же способ управления реальными объектами для взаимодействия с виртуальными.</span><span class="sxs-lookup"><span data-stu-id="cf58d-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="cf58d-118">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="cf58d-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="cf58d-119">Такое модальность позволяет пользователям взаимодействовать с голограммами на расстоянии.</span><span class="sxs-lookup"><span data-stu-id="cf58d-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="cf58d-120">Он позволяет пользователям лучше использовать окружающую подстановку.</span><span class="sxs-lookup"><span data-stu-id="cf58d-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="cf58d-121">Пользователи могут размещать голограммы в любом месте и по-прежнему обращаться к ним с любых расстояний.</span><span class="sxs-lookup"><span data-stu-id="cf58d-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="cf58d-122">Модели и жесты, используемые для управления и манипулирования плоскими и трехмерными голограммами, высоко синхронизированы с этими моделями с прямой манипуляцией.</span><span class="sxs-lookup"><span data-stu-id="cf58d-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="cf58d-123">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="cf58d-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="cf58d-124">Контроллеры движения — это средства, расширяющие физические возможности пользователя путем предоставления точных взаимодействий между большим диапазоном расстояний при использовании одной или обеих стрелок.</span><span class="sxs-lookup"><span data-stu-id="cf58d-124">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="cf58d-125">Эти аксессуары оборудования предоставляют ярлыки для многих часто используемых взаимодействий и предоставляют сурефутед, тактиле Отзывы о различных действиях.</span><span class="sxs-lookup"><span data-stu-id="cf58d-125">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="cf58d-126">В настоящее время контроллеры движения доступны только для сценариев Windows Mixed Reality (ВМР).</span><span class="sxs-lookup"><span data-stu-id="cf58d-126">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 

![Сравнение перемещения и контроллеров движения модальностей](images/Hands-and-controllers-720px.jpg)<br>

<span data-ttu-id="cf58d-128">*Сравнение перемещения и контроллеров движения модальностей*</span><span class="sxs-lookup"><span data-stu-id="cf58d-128">*Comparison of hands and motion controllers modalities*</span></span>

## <a name="see-also"></a><span data-ttu-id="cf58d-129">См. также</span><span class="sxs-lookup"><span data-stu-id="cf58d-129">See also</span></span>
* [<span data-ttu-id="cf58d-130">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="cf58d-130">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="cf58d-131">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="cf58d-131">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="cf58d-132">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="cf58d-132">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cf58d-133">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="cf58d-133">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="cf58d-134">Режимы без использования рук</span><span class="sxs-lookup"><span data-stu-id="cf58d-134">Hands-free</span></span>](hands-free.md)
