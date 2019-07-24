---
title: Отображение хода выполнения
description: Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, проектирование, элементы управления, Пользовательский интерфейс, UX
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523253"
---
# <a name="displaying-progress"></a><span data-ttu-id="fa81e-104">Отображение хода выполнения</span><span class="sxs-lookup"><span data-stu-id="fa81e-104">Displaying progress</span></span>

<span data-ttu-id="fa81e-105">Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.</span><span class="sxs-lookup"><span data-stu-id="fa81e-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="fa81e-106">Это может означать, что пользователь не сможет взаимодействовать с приложением, когда индикатор выполнения отображается. Также в зависимости от того, какой индикатор используется, он может отображать время ожидания.</span><span class="sxs-lookup"><span data-stu-id="fa81e-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="fa81e-107">![Пример круга хода выполнения в HoloLens](images/HoloLens2_Loader.gif)</span><span class="sxs-lookup"><span data-stu-id="fa81e-107">![Progress ring example in HoloLens](images/HoloLens2_Loader.gif)</span></span><br>
<span data-ttu-id="fa81e-108">*Пример круга хода выполнения в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="fa81e-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="fa81e-109">Типы хода выполнения</span><span class="sxs-lookup"><span data-stu-id="fa81e-109">Types of progress</span></span>

<span data-ttu-id="fa81e-110">Важно предоставить пользователю сведения о том, что происходит.</span><span class="sxs-lookup"><span data-stu-id="fa81e-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="fa81e-111">Пользователи в смешанной реальности могут легко отвлекаться от физических сред или объектов, если ваше приложение не обеспечивает хорошую визуальную обратную связь.</span><span class="sxs-lookup"><span data-stu-id="fa81e-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="fa81e-112">В ситуациях, которые могут занять несколько секунд, например при загрузке данных или при обновлении сцены, рекомендуется отобразить визуальный индикатор.</span><span class="sxs-lookup"><span data-stu-id="fa81e-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="fa81e-113">Существует два варианта отображения пользователя, выполняющего операцию — **индикатор выполнения** или **круг хода выполнения**.</span><span class="sxs-lookup"><span data-stu-id="fa81e-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="fa81e-114">Индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="fa81e-114">Progress bar</span></span>

![Пример индикатора выполнения в HoloLens](images/640px-progressbar.jpg)

<span data-ttu-id="fa81e-116">Индикатор выполнения показывает процент завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="fa81e-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="fa81e-117">Его следует использовать во время операции, длительность которой известен (прерывается), но ход выполнения не должен блокировать взаимодействие пользователя с приложением.</span><span class="sxs-lookup"><span data-stu-id="fa81e-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="fa81e-118">Кольцевой индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="fa81e-118">Progress ring</span></span>

![Пример круга хода выполнения в HoloLens](images/640px-progressring.jpg)

<span data-ttu-id="fa81e-120">Круг выполнения имеет неопределенное состояние, и его следует использовать, когда любое дальнейшее взаимодействие с пользователем блокируется до завершения операции.</span><span class="sxs-lookup"><span data-stu-id="fa81e-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="fa81e-121">Ход выполнения с пользовательским объектом</span><span class="sxs-lookup"><span data-stu-id="fa81e-121">Progress with a custom object</span></span>

![Пример нестандартной сетки в HoloLens](images/640px-progresscustom.jpg)

<span data-ttu-id="fa81e-123">Вы можете добавить в свое собственное удостоверение приложения и фирменную символику, настроив управление ходом выполнения с помощью собственных двумерных или трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="fa81e-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="fa81e-124">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="fa81e-124">Best practices</span></span>
* <span data-ttu-id="fa81e-125">Тесное связывание [объявления или тега](billboarding-and-tag-along.md) с отображением хода выполнения, так как пользователь может легко переместить свой заголовок в пустое место и потерять контекст.</span><span class="sxs-lookup"><span data-stu-id="fa81e-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="fa81e-126">Приложение может выглядеть аварийно, если пользователь не увидит ничего.</span><span class="sxs-lookup"><span data-stu-id="fa81e-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="fa81e-127">Всплывающие окна и теги встроены в prefab хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="fa81e-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="fa81e-128">Всегда удобно предоставлять сведения о состоянии, что происходит с пользователем.</span><span class="sxs-lookup"><span data-stu-id="fa81e-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="fa81e-129">Prefab выполнения предоставляет различные визуальные стили, включая ход выполнения стандартного звонка Windows для предоставления состояния.</span><span class="sxs-lookup"><span data-stu-id="fa81e-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="fa81e-130">Вы также можете использовать настраиваемую сетку с анимацией, если хотите, чтобы стиль выполнения совпадал с торговой маркой приложения.</span><span class="sxs-lookup"><span data-stu-id="fa81e-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa81e-131">См. также</span><span class="sxs-lookup"><span data-stu-id="fa81e-131">See also</span></span>
* [<span data-ttu-id="fa81e-132">Сценарии хода выполнения и Prefabs в наборе средств смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="fa81e-132">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="fa81e-133">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="fa81e-133">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="fa81e-134">Активный объект</span><span class="sxs-lookup"><span data-stu-id="fa81e-134">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="fa81e-135">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="fa81e-135">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="fa81e-136">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="fa81e-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
