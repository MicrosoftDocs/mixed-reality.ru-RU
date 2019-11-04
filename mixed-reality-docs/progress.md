---
title: Отображение хода выполнения
description: Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, проектирование, элементы управления, Пользовательский интерфейс, UX
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437537"
---
# <a name="displaying-progress"></a><span data-ttu-id="06b48-104">Отображение хода выполнения</span><span class="sxs-lookup"><span data-stu-id="06b48-104">Displaying progress</span></span>

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="06b48-105">Элемент управления "Ход выполнения" служит для уведомления пользователя о том, что выполняется длительная операция.</span><span class="sxs-lookup"><span data-stu-id="06b48-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="06b48-106">Это может означать, что пользователь не сможет взаимодействовать с приложением, когда индикатор выполнения отображается. Также в зависимости от того, какой индикатор используется, он может отображать время ожидания.</span><span class="sxs-lookup"><span data-stu-id="06b48-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="06b48-107">Типы хода выполнения</span><span class="sxs-lookup"><span data-stu-id="06b48-107">Types of progress</span></span>

<span data-ttu-id="06b48-108">Важно предоставить пользователю сведения о том, что происходит.</span><span class="sxs-lookup"><span data-stu-id="06b48-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="06b48-109">Пользователи в смешанной реальности могут легко отвлекаться от физических сред или объектов, если ваше приложение не обеспечивает хорошую визуальную обратную связь.</span><span class="sxs-lookup"><span data-stu-id="06b48-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="06b48-110">В ситуациях, которые могут занять несколько секунд, например при загрузке данных или при обновлении сцены, рекомендуется отобразить визуальный индикатор.</span><span class="sxs-lookup"><span data-stu-id="06b48-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="06b48-111">Существует два варианта отображения пользователя, выполняющего операцию — **индикатор выполнения** или **круг хода выполнения**.</span><span class="sxs-lookup"><span data-stu-id="06b48-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="06b48-112">Индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="06b48-112">Progress bar</span></span><br>
        <span data-ttu-id="06b48-113">Индикатор выполнения показывает процент завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="06b48-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="06b48-114">Его следует использовать во время операции, длительность которой известен (прерывается), но ход выполнения не должен блокировать взаимодействие пользователя с приложением.</span><span class="sxs-lookup"><span data-stu-id="06b48-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="06b48-115">*Изображение: пример индикатора выполнения в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="06b48-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="06b48-116">![пространство](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="06b48-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="06b48-117">![пример индикатора выполнения в HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="06b48-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="06b48-118">Кольцевой индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="06b48-118">Progress ring</span></span><br>
        <span data-ttu-id="06b48-119">Круг выполнения имеет неопределенное состояние, и его следует использовать, когда любое дальнейшее взаимодействие с пользователем блокируется до завершения операции.</span><span class="sxs-lookup"><span data-stu-id="06b48-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="06b48-120">*Изображение: пример круга хода выполнения в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="06b48-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="06b48-121">![пространство](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="06b48-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="06b48-122">Пример круга хода выполнения ![в HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="06b48-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="06b48-123">Ход выполнения с пользовательским объектом</span><span class="sxs-lookup"><span data-stu-id="06b48-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="06b48-124">Вы можете добавить в свое собственное удостоверение приложения и фирменную символику, настроив управление ходом выполнения с помощью собственных двумерных или трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="06b48-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="06b48-125">*Изображение: ход выполнения с примером настраиваемой сетки в HoloLens*</span><span class="sxs-lookup"><span data-stu-id="06b48-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="06b48-126">![пространство](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="06b48-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="06b48-127">![хода выполнения с помощью пользовательского примера сетки в HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="06b48-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="06b48-128">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="06b48-128">Best practices</span></span>
* <span data-ttu-id="06b48-129">Тесное связывание [объявления или тега](billboarding-and-tag-along.md) с отображением хода выполнения, так как пользователь может легко переместить свой заголовок в пустое место и потерять контекст.</span><span class="sxs-lookup"><span data-stu-id="06b48-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="06b48-130">Приложение может выглядеть аварийно, если пользователь не увидит ничего.</span><span class="sxs-lookup"><span data-stu-id="06b48-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="06b48-131">Всплывающие окна и теги встроены в prefab хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="06b48-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="06b48-132">Всегда удобно предоставлять сведения о состоянии, что происходит с пользователем.</span><span class="sxs-lookup"><span data-stu-id="06b48-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="06b48-133">Prefab выполнения предоставляет различные визуальные стили, включая ход выполнения стандартного звонка Windows для предоставления состояния.</span><span class="sxs-lookup"><span data-stu-id="06b48-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="06b48-134">Вы также можете использовать настраиваемую сетку с анимацией, если хотите, чтобы стиль выполнения совпадал с торговой маркой приложения.</span><span class="sxs-lookup"><span data-stu-id="06b48-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="06b48-135">См. также</span><span class="sxs-lookup"><span data-stu-id="06b48-135">See also</span></span>
* [<span data-ttu-id="06b48-136">Сценарии хода выполнения и Prefabs в наборе средств смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="06b48-136">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="06b48-137">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="06b48-137">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="06b48-138">Активный объект</span><span class="sxs-lookup"><span data-stu-id="06b48-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="06b48-139">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="06b48-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="06b48-140">Биллбординг и закрепление элемента в пространстве</span><span class="sxs-lookup"><span data-stu-id="06b48-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
