---
title: Отображение хода выполнения
description: Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, разработки, элементы управления, пользовательский интерфейс, ux
ms.openlocfilehash: 9edddc7800f0d7334d1ceba97b9a06fd6d4580ac
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603215"
---
# <a name="displaying-progress"></a><span data-ttu-id="74a5f-104">Отображение хода выполнения</span><span class="sxs-lookup"><span data-stu-id="74a5f-104">Displaying progress</span></span>

<span data-ttu-id="74a5f-105">Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.</span><span class="sxs-lookup"><span data-stu-id="74a5f-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="74a5f-106">Это может означать, что пользователь не сможет взаимодействовать с приложением, когда индикатор выполнения отображается. Также в зависимости от того, какой индикатор используется, он может отображать время ожидания.</span><span class="sxs-lookup"><span data-stu-id="74a5f-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="74a5f-107">![Пример кольца хода выполнения в HoloLens](images/640px-progress-hero.jpg)</span><span class="sxs-lookup"><span data-stu-id="74a5f-107">![Progress ring example in HoloLens](images/640px-progress-hero.jpg)</span></span><br>
<span data-ttu-id="74a5f-108">*Пример кольца хода выполнения в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="74a5f-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="74a5f-109">Типы хода выполнения</span><span class="sxs-lookup"><span data-stu-id="74a5f-109">Types of progress</span></span>

<span data-ttu-id="74a5f-110">Важно предоставить сведения о пользователе, о том, что происходит.</span><span class="sxs-lookup"><span data-stu-id="74a5f-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="74a5f-111">В смешанной реальности пользователей может быть легко избежать физической среды или объектами Если приложение не дает хороший визуальную обратную связь.</span><span class="sxs-lookup"><span data-stu-id="74a5f-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="74a5f-112">В ситуациях, которые принимают несколько секунд выполняется обновление таких данных во время загрузки или сцены, имеет смысл для отображения визуального индикатора.</span><span class="sxs-lookup"><span data-stu-id="74a5f-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="74a5f-113">Существует два варианта для представления пользователю, что операция выполняется — **индикатор** или **кольца хода выполнения**.</span><span class="sxs-lookup"><span data-stu-id="74a5f-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="74a5f-114">Индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="74a5f-114">Progress bar</span></span>

![Пример панели хода выполнения в HoloLens](images/640px-progressbar.jpg)

<span data-ttu-id="74a5f-116">Индикатор хода выполнения показывает процент завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="74a5f-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="74a5f-117">Он должен использоваться при выполнении операции, длительность которого известен (определенный), но ход его выполнения не должны блокировать взаимодействия пользователя с приложением.</span><span class="sxs-lookup"><span data-stu-id="74a5f-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="74a5f-118">Кольцевой индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="74a5f-118">Progress ring</span></span>

![Пример кольца хода выполнения в HoloLens](images/640px-progressring.jpg)

<span data-ttu-id="74a5f-120">Кольца хода выполнения только имеет неопределенное состояние и следует использовать, если все последующие взаимодействия пользователя блокируется до завершения операции.</span><span class="sxs-lookup"><span data-stu-id="74a5f-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="74a5f-121">Ход выполнения с помощью пользовательского объекта</span><span class="sxs-lookup"><span data-stu-id="74a5f-121">Progress with a custom object</span></span>

![Ход выполнения с помощью примера пользовательского сетки в HoloLens](images/640px-progresscustom.jpg)

<span data-ttu-id="74a5f-123">Можно добавить для персональной и фирменные приложения путем настройки индикатора хода выполнения с помощью собственных пользовательских двухмерных и трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="74a5f-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="74a5f-124">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="74a5f-124">Best practices</span></span>
* <span data-ttu-id="74a5f-125">Тесно связать [биллбординга или tag-along](billboarding-and-tag-along.md) для отображения хода выполнения, так как пользователь может легко переместить их головах в пустое место и терять контекст.</span><span class="sxs-lookup"><span data-stu-id="74a5f-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="74a5f-126">Приложение может выглядеть он произошел, если пользователь не видит никаких действий.</span><span class="sxs-lookup"><span data-stu-id="74a5f-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="74a5f-127">Billboarding и tag-along встроена в prefab хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="74a5f-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="74a5f-128">Всегда рекомендуется предоставлять сведения о состоянии о происходящем для пользователя.</span><span class="sxs-lookup"><span data-stu-id="74a5f-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="74a5f-129">Ход выполнения prefab предоставляет различные стили оформления, включая предоставление состояния процесса выполнения стандартных типу кольцевого Windows.</span><span class="sxs-lookup"><span data-stu-id="74a5f-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="74a5f-130">Также можно использовать пользовательские сетки с анимацией Если стиль ход выравнивание по торговой марки вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="74a5f-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="74a5f-131">См. также</span><span class="sxs-lookup"><span data-stu-id="74a5f-131">See also</span></span>
* [<span data-ttu-id="74a5f-132">Сценарии и prefabs для отслеживания хода выполнения, о наборе средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="74a5f-132">Scripts and prefabs for Progress on Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ProgressExample.md)
* [<span data-ttu-id="74a5f-133">Элементом объекта</span><span class="sxs-lookup"><span data-stu-id="74a5f-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="74a5f-134">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="74a5f-134">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="74a5f-135">Биллбординга и tag-along</span><span class="sxs-lookup"><span data-stu-id="74a5f-135">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
