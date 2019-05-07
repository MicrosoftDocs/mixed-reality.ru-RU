---
title: Руки и контроллеры движения
description: Общие сведения о руки и взаимодействие с контроллерами движения
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Смешанной реальности, руки, контроллеров движения, взаимодействие, проектирование
ms.openlocfilehash: 583d284ee98b8ccbc0a9c2c8670551d0a7397074
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873996"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="ab167-104">Руки и контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="ab167-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="ab167-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="ab167-105">Scenarios</span></span>
<span data-ttu-id="ab167-106">Если вы решили внедрить модели взаимодействия после чтения [правила разработки](interaction-fundamentals.md), это означает, что вы разрабатываете приложение так, чтобы пользователям использовать две руки для взаимодействия с внешним миром holographic.</span><span class="sxs-lookup"><span data-stu-id="ab167-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="ab167-107">Приложение собирается для достижения этой цели удаления boundry между виртуальными и физическими.</span><span class="sxs-lookup"><span data-stu-id="ab167-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="ab167-108">Возможно, некоторые сценарии:</span><span class="sxs-lookup"><span data-stu-id="ab167-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="ab167-109">Предоставляя сведения работников 2D виртуальный экраны и пользовательских интерфейсов для отображения и содержимое элемента управления</span><span class="sxs-lookup"><span data-stu-id="ab167-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="ab167-110">Предоставление руководства работников первой строки и структур в линии сборки фабрики</span><span class="sxs-lookup"><span data-stu-id="ab167-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="ab167-111">Разработка профессиональных инструментов для помощь и обучение поликлиники</span><span class="sxs-lookup"><span data-stu-id="ab167-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="ab167-112">С помощью 3D виртуальных объектах для оформления реальном мире или создание второй системы</span><span class="sxs-lookup"><span data-stu-id="ab167-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="ab167-113">Расположения и на основе служб игры с помощью реального мира в качестве фона</span><span class="sxs-lookup"><span data-stu-id="ab167-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="ab167-114">Руки и модальностей контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="ab167-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-near-hand-interactiondirect-manipulationmd"></a>[<span data-ttu-id="ab167-115">Прямые манипуляции (рядом с правым взаимодействия вручную)</span><span class="sxs-lookup"><span data-stu-id="ab167-115">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
<span data-ttu-id="ab167-116">Это связано с эффективностью руки, с которыми пользователи способны прикосновения и прямое управление голограммы модальность.</span><span class="sxs-lookup"><span data-stu-id="ab167-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="ab167-117">По leaveraging конфигураций повседневную жизнь и программное обеспечение правильной visual читаемости, пользователи могут использовать для взаимодействия с виртуальной из них так же управления объекты реального мира.</span><span class="sxs-lookup"><span data-stu-id="ab167-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world obejcts to interact with virtual ones.</span></span>   

### <a name="point-and-commit-far-hand-interactionpoint-and-commitmd"></a>[<span data-ttu-id="ab167-118">Точки, чтобы зафиксировать (Far взаимодействия вручную)</span><span class="sxs-lookup"><span data-stu-id="ab167-118">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
<span data-ttu-id="ab167-119">Этот модальность предоставляет пользователям super power для взаимодействия с голограммы в расстояние.</span><span class="sxs-lookup"><span data-stu-id="ab167-119">This modality provides users super power to interact with holograms in a distance.</span></span> <span data-ttu-id="ab167-120">Он позволяет пользователям наиболее эффективно использовать параметр окружающего.</span><span class="sxs-lookup"><span data-stu-id="ab167-120">It enables users to make the best use of setting of surrounding.</span></span> <span data-ttu-id="ab167-121">Пользователей можно разместить в любом голограммы и можно по-прежнему обращаться к ним с любого расстояния.</span><span class="sxs-lookup"><span data-stu-id="ab167-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="ab167-122">Ментальных моделей и жесты для контроля и управления ими голограммы 2D и 3D синхронизированы высокой с соответствующими прямого управления.</span><span class="sxs-lookup"><span data-stu-id="ab167-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="ab167-123">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="ab167-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="ab167-124">Контроллеры движения, средства, которые расширяют возможности пользователей, предоставляя точные взаимодействия через разнообразные расстояния при использовании одного или обоих руки.</span><span class="sxs-lookup"><span data-stu-id="ab167-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="ab167-125">Эти стандартные оборудования позволяют многие часто используемые взаимодействия и дает surefooted, tactile обратной связи для различных действий.</span><span class="sxs-lookup"><span data-stu-id="ab167-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="ab167-126">В настоящее время движения контроллеров доступны только для сценариев WMR.</span><span class="sxs-lookup"><span data-stu-id="ab167-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="ab167-127">См. также</span><span class="sxs-lookup"><span data-stu-id="ab167-127">See also</span></span>
* [<span data-ttu-id="ab167-128">Взглядом и фиксации</span><span class="sxs-lookup"><span data-stu-id="ab167-128">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ab167-129">Прямые манипуляции (рядом с правым взаимодействия вручную)</span><span class="sxs-lookup"><span data-stu-id="ab167-129">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ab167-130">Точки, чтобы зафиксировать (Far взаимодействия вручную)</span><span class="sxs-lookup"><span data-stu-id="ab167-130">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
* [<span data-ttu-id="ab167-131">Без участия пользователя</span><span class="sxs-lookup"><span data-stu-id="ab167-131">Hands-free</span></span>](hands-free.md)
* [<span data-ttu-id="ab167-132">Нацеливание взглядом</span><span class="sxs-lookup"><span data-stu-id="ab167-132">Gaze targeting</span></span>](gaze-targeting.md)
