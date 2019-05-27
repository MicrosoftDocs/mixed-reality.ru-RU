---
title: Руки и контроллеры движения
description: Общие сведения о руки и взаимодействие с контроллерами движения
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Смешанной реальности, руки, контроллеров движения, взаимодействие, проектирование
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039169"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="4bbe0-104">Руки и контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="4bbe0-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="4bbe0-105">Сценарии</span><span class="sxs-lookup"><span data-stu-id="4bbe0-105">Scenarios</span></span>
<span data-ttu-id="4bbe0-106">Если вы решили внедрить модели взаимодействия после чтения [правила разработки](interaction-fundamentals.md), это означает, что вы разрабатываете приложение так, чтобы пользователям использовать две руки для взаимодействия с внешним миром holographic.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="4bbe0-107">Приложение собирается для достижения этой цели удаления boundry между виртуальными и физическими.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="4bbe0-108">Возможно, некоторые сценарии:</span><span class="sxs-lookup"><span data-stu-id="4bbe0-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="4bbe0-109">Предоставляя сведения работников 2D виртуальный экраны и пользовательских интерфейсов для отображения и содержимое элемента управления</span><span class="sxs-lookup"><span data-stu-id="4bbe0-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="4bbe0-110">Предоставление руководства работников первой строки и структур в линии сборки фабрики</span><span class="sxs-lookup"><span data-stu-id="4bbe0-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="4bbe0-111">Разработка профессиональных инструментов для помощь и обучение поликлиники</span><span class="sxs-lookup"><span data-stu-id="4bbe0-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="4bbe0-112">С помощью 3D виртуальных объектах для оформления реальном мире или создание второй системы</span><span class="sxs-lookup"><span data-stu-id="4bbe0-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="4bbe0-113">Расположения и на основе служб игры с помощью реального мира в качестве фона</span><span class="sxs-lookup"><span data-stu-id="4bbe0-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="4bbe0-114">Руки и модальностей контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="4bbe0-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="4bbe0-115">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="4bbe0-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="4bbe0-116">Это связано с эффективностью руки, с которыми пользователи способны прикосновения и прямое управление голограммы модальность.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="4bbe0-117">По leaveraging конфигураций повседневную жизнь и программное обеспечение правильной visual читаемости, пользователи могут использовать для взаимодействия с виртуальной из них так же, обработка объектов реального мира.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="4bbe0-118">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="4bbe0-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="4bbe0-119">Этот модальность позволяет пользователям взаимодействовать с голограммы в расстояние.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="4bbe0-120">Он позволяет пользователям наиболее эффективно использовать окружающей среды.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="4bbe0-121">Пользователей можно разместить в любом голограммы и можно по-прежнему обращаться к ним с любого расстояния.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="4bbe0-122">Ментальных моделей и жесты для контроля и управления ими голограммы 2D и 3D синхронизированы высокой с соответствующими прямого управления.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="4bbe0-123">Контроллеры движения</span><span class="sxs-lookup"><span data-stu-id="4bbe0-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="4bbe0-124">Контроллеры движения, средства, которые расширяют возможности пользователей, предоставляя точные взаимодействия через разнообразные расстояния при использовании одного или обоих руки.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="4bbe0-125">Эти стандартные оборудования позволяют многие часто используемые взаимодействия и дает surefooted, tactile обратной связи для различных действий.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="4bbe0-126">В настоящее время движения контроллеров доступны только для сценариев WMR.</span><span class="sxs-lookup"><span data-stu-id="4bbe0-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="4bbe0-127">См. также</span><span class="sxs-lookup"><span data-stu-id="4bbe0-127">See also</span></span>
* [<span data-ttu-id="4bbe0-128">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="4bbe0-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="4bbe0-129">Направление головы и остановка</span><span class="sxs-lookup"><span data-stu-id="4bbe0-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="4bbe0-130">Непосредственное манипулирование с использованием рук</span><span class="sxs-lookup"><span data-stu-id="4bbe0-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4bbe0-131">Наведение и фиксация с использованием рук</span><span class="sxs-lookup"><span data-stu-id="4bbe0-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="4bbe0-132">Режимы без использования рук</span><span class="sxs-lookup"><span data-stu-id="4bbe0-132">Hands-free</span></span>](hands-free.md)
