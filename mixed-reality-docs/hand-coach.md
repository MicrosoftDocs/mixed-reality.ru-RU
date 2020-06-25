---
title: Обучение вручную
description: Трехмерные руки, активируемые, когда система не обнаруживает руки пользователя, которые помогут им помочь.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, проектирование, рука, увлекательная гарнитура, МРТК, руки, помощь
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345672"
---
# <a name="hand-coach"></a><span data-ttu-id="6ddb3-104">Обучение вручную</span><span class="sxs-lookup"><span data-stu-id="6ddb3-104">Hand coach</span></span>
![Пример: рука](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="6ddb3-106">Руки — это трехмерные модели, которые запускаются, когда система не обнаруживает руки пользователя.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-106">Hand coach is 3D modeled hands that are triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="6ddb3-107">Это реализовано как компонент обучения, который помогает пользователю, когда жест не научился.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-107">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="6ddb3-108">Если пользователь не выполнил указанный жест в течение периода, руки будут циклически заканчиваться с задержкой.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-108">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="6ddb3-109">Для представления нажатия кнопки или выбора голограммы можно использовать руку.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="6ddb3-110">Предоставленная консультационная рука</span><span class="sxs-lookup"><span data-stu-id="6ddb3-110">Hand coach provided</span></span>

<span data-ttu-id="6ddb3-111">Текущая модель взаимодействия представляет широкий спектр элементов управления жестами, таких как прокрутка, дальнее выделение и близко к касанию.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="6ddb3-112">Ниже приведен полный список существующих жестов руки, представленных в<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> мртк</a>.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="6ddb3-113">![Пример приближения к SELECT](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="6ddb3-114">**Пример вблизи Select — показывает, как выбрать кнопки или закрыть взаимодействующие объекты**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6ddb3-115">![Пример воздушного касания](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="6ddb3-116">**Пример Air TAP — используется для демонстрации выбора объектов, которые находятся далеко**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6ddb3-117">![Пример перемещения](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="6ddb3-118">**Пример перемещения объекта в пространстве — используется для демонстрации перемещения голограммы в пространстве**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6ddb3-119">![Пример поворота](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="6ddb3-120">**Пример поворота — используется для демонстрации поворота голограмм или объектов**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="6ddb3-121">![Пример масштабирования](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="6ddb3-122">**Пример масштабирования — используется для демонстрации того, как можно управлять голограммами, чтобы они были больше или меньше**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6ddb3-123">![Пример Palm up](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="6ddb3-124">**Пример использования Palm — предлагаемое использование для открытия меню "руки"**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6ddb3-125">![Пример Хандфлип](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="6ddb3-126">**Примере с перелистыванием вручную — другой способ открыть меню "руки"**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6ddb3-127">![Пример прокрутки](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="6ddb3-128">**Пример прокрутки — используется для прокрутки списка или длинного документа**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="6ddb3-129">Принципы проектирования</span><span class="sxs-lookup"><span data-stu-id="6ddb3-129">Design concepts</span></span>

<span data-ttu-id="6ddb3-130">Для Hololens2 мы разработали взаимодействия, основанные на инстинктуал и естественных жестах руки.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="6ddb3-131">Мы считаем, что они интуитивно понятны большинству пользователей, и, таким способом, не создают выделенные данные для обучения жестов.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-131">We believe these to be intuitive to most users and thus did not create dedicated gesture learning moments.</span></span> <span data-ttu-id="6ddb3-132">Вместо этого мы создали свою помощь, чтобы помочь пользователям, которые могут задержаться или не знакомы с голограммами, узнать об этих жестах.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-132">Instead, we created the hand coach to help users who might get stuck or are unfamiliar with interacting with holograms learn about these gestures.</span></span> <span data-ttu-id="6ddb3-133">Без обучения мы продемонстрировали, что пользователи покажут, как выполнить действие, выполнив демонстрацию, что это лучший вариант.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="6ddb3-134">Во всех наших исследованиях было обнаружено, что пользователи смогли понять жест, но требовалось небольшое руководство.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-134">In our studies, we found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="6ddb3-135">Если бы мы определили, что пользователь не взаимодействует с объектом в течение периода, будет запущено обучение руки, которое демонстрирует правильное размещение и положение пальца.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-135">If we detect that a user does not interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="6ddb3-136">Точки</span><span class="sxs-lookup"><span data-stu-id="6ddb3-136">Intuitive</span></span>

<span data-ttu-id="6ddb3-137">При анимации рук они должны быть очевидны и шаудн'т вызывать путаницу.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-137">When animating hands, it should be obvious and shoudn't cause any confusion.</span></span> <span data-ttu-id="6ddb3-138">Анимация руки — это представление жеста, который вы пытаетесь вызвать пользователю, чтобы понять его назначение.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-138">The animation of the hands is a representation of the gesture your trying to evoke to the user to understand it's purpose.</span></span> 

<span data-ttu-id="6ddb3-139">Например, если вы хотите, чтобы пользователь нажмет кнопку, будет активирована рука, нажатие кнопки.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="6ddb3-140">![Пример: близкое касание](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="6ddb3-141">*Практические примеры, демонстрирующие касание драгоценного камень*</span><span class="sxs-lookup"><span data-stu-id="6ddb3-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="6ddb3-142">Масштаб вручную</span><span class="sxs-lookup"><span data-stu-id="6ddb3-142">Hand scale</span></span>

<span data-ttu-id="6ddb3-143">Мы протестировали различные размеры с помощью меню пользовательского интерфейса и заказалось, что если бы у руки было истинное изменение размера, это менаЦинго, но если бы они оказались слишком маленькими, то трудно увидеть и понять жест.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling but if they were too small then it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="6ddb3-144">**Голоса и руки**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-144">**Voice over and hands**</span></span>

<span data-ttu-id="6ddb3-145">Не ожидается, что пользователи могут прослушивать один набор инструкций с помощью голоса, а также просматривать различные инструкции с помощью руки.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-145">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="6ddb3-146">Поочередно изменяйте свои инструкции, чтобы помочь пользователям сосредоточиться на снижении перегрузки датчиков.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-146">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="6ddb3-147">Можно ли создать собственную?</span><span class="sxs-lookup"><span data-stu-id="6ddb3-147">Can I create my own?</span></span>

<span data-ttu-id="6ddb3-148">Да.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-148">Yes!</span></span> <span data-ttu-id="6ddb3-149">Мы рекомендуем вам создать собственный уникальный жест для игры и участвовать в сообществе!</span><span class="sxs-lookup"><span data-stu-id="6ddb3-149">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="6ddb3-150">Мы предоставили Maya-файл с определенной нагрузкой, который можно использовать для приложения, который можно скачать здесь: <a href="files/HandCoach_MRTK.zip">скачать HandCoach_MRTK.zip</a></span><span class="sxs-lookup"><span data-stu-id="6ddb3-150">We have provided a Maya file of a Rigged hand that can be used for your app which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip</a></span></span>

<span data-ttu-id="6ddb3-151">![Пример анимированных рук в Maya](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-151">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="6ddb3-152">*Пример анимационной руки, знакомство Box в Maya*</span><span class="sxs-lookup"><span data-stu-id="6ddb3-152">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="6ddb3-153">**Рекомендуемое средство разработки**</span><span class="sxs-lookup"><span data-stu-id="6ddb3-153">**Recommended authoring tool**</span></span>

<span data-ttu-id="6ddb3-154">Многие из трехмерных исполнителей используют [Maya Autodesk, который может использовать HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) для преобразования способа создания ресурсов.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-154">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="6ddb3-155">Файл руки — это двоичный файл Maya, поэтому рекомендуется использовать Maya для анимации и экспорта стрелок.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-155">The hands file provided is a Maya Binary File, so it is recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="6ddb3-156">Если вы предпочитаете использовать другую трехмерную программу, см <b>. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">Скачайте HandCoachMRTK_FBX.zip</a> , чтобы создать собственную установку контроллера.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-156">If you prefer to use another 3D program, here is a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">           Download HandCoachMRTK_FBX.zip</a> to create your own controller setup.</span></span> 

<span data-ttu-id="6ddb3-157">Если вы используете доступный для загрузки файл руки Maya, рекомендуется масштабировать руки в Unity до 0,6.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-157">If using the downloadable maya Hand File provided, it is suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="6ddb3-158">![Пример: высокоMayaная платформа для подготовки к сдаче](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-158">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="6ddb3-159">*Руки с Спецоснастка*</span><span class="sxs-lookup"><span data-stu-id="6ddb3-159">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="6ddb3-160">Технические спецификации</span><span class="sxs-lookup"><span data-stu-id="6ddb3-160">Technical Specs</span></span>

*   <span data-ttu-id="6ddb3-161">Два переданного файла доступны в формате ASCII Maya</span><span class="sxs-lookup"><span data-stu-id="6ddb3-161">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="6ddb3-162">Правая и левая рука доступны в двоичном формате Maya</span><span class="sxs-lookup"><span data-stu-id="6ddb3-162">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="6ddb3-163">Задайте для файла Maya значение 24 кадров/с</span><span class="sxs-lookup"><span data-stu-id="6ddb3-163">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="6ddb3-164">В файле имеется левая и правая рука, которые можно использовать для двух перенаправленных или однопользовательских жестов.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-164">Within the file, there is a left and right hand which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="6ddb3-165">Правая рука отображается по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-165">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="6ddb3-166">Рекомендуется оставить буфер около 10 кадров в начале и в конце для появления.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-166">It is suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="6ddb3-167">При анимации объекта с указанным целевым объектом рекомендуется анимировать его в поле по умолчанию или значение null.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-167">If animating a object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="6ddb3-168">Если рука выполняет анимацию физического объекта, такого как Box, рекомендуется не анимировать перевод в Maya, но дожидаться анимации в Unity или в коде.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-168">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="6ddb3-169">Видимая анимация должна составлять 1,5 с для получения значимой информации</span><span class="sxs-lookup"><span data-stu-id="6ddb3-169">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="6ddb3-170">Когда вы довольны анимацией:</span><span class="sxs-lookup"><span data-stu-id="6ddb3-170">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="6ddb3-171">Выбор всех соединений и внедрить ключевых кадров</span><span class="sxs-lookup"><span data-stu-id="6ddb3-171">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="6ddb3-172">Удаление контроллеров, выбор соединений и сетки и экспорт в качестве FBX</span><span class="sxs-lookup"><span data-stu-id="6ddb3-172">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="6ddb3-173">При наличии нескольких анимаций можно использовать встроенную средство экспорта игр Maya:https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="6ddb3-173">If there are Multiple Animations, you can use Maya’s built in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="6ddb3-174">Экспорт из Maya</span><span class="sxs-lookup"><span data-stu-id="6ddb3-174">Exporting from Maya</span></span>

<span data-ttu-id="6ddb3-175">Когда вы удовлетворены анимацией</span><span class="sxs-lookup"><span data-stu-id="6ddb3-175">After you are satisfied with your animation</span></span>
* <span data-ttu-id="6ddb3-176">Выбрать все соединения: выбрать иерархию ></span><span class="sxs-lookup"><span data-stu-id="6ddb3-176">Select all joints: Select > Hierarchy</span></span>

     ![Пример: расположение меню](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="6ddb3-178">Внедрить анимации: переключение на анимацию > ключ > анимация внедрить</span><span class="sxs-lookup"><span data-stu-id="6ddb3-178">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![Пример: расположение меню](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="6ddb3-180">Удалить платформу контроллера: > MainR_Grp или MainL_Grp</span><span class="sxs-lookup"><span data-stu-id="6ddb3-180">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![Пример: расположение меню](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="6ddb3-182">Экспортировать как FBX: выберите JNT + сеток: файл > экспорт выбор (флажок) > выбор экспорта</span><span class="sxs-lookup"><span data-stu-id="6ddb3-182">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![Пример: расположение меню](images/HandCoach/OptionBox.png)<br>

     ![Пример: расположение меню](images/HandCoach/SelectionExport.png)<br>

     ![Пример: расположение меню](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="6ddb3-186">При экспорте в FBX и внесении в Unity масштабирование осуществляется до 0,6.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-186">When exporting as a FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="6ddb3-187">Мы обнаружили, что это был идеальный баланс для отображения рук.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-187">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="6ddb3-188">![Пример: параметры Unity](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="6ddb3-188">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="6ddb3-189">*Параметры Unity для HandCoach_R prefab найдены в МРТК*</span><span class="sxs-lookup"><span data-stu-id="6ddb3-189">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="6ddb3-190">Реализация руки в проекте Unity</span><span class="sxs-lookup"><span data-stu-id="6ddb3-190">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="6ddb3-191">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="6ddb3-191">Best practices</span></span>
*    <span data-ttu-id="6ddb3-192">Рекомендуется масштабировать руки в Unity до 0,6</span><span class="sxs-lookup"><span data-stu-id="6ddb3-192">It is suggested to scale down the hands in unity to 0.6</span></span>
*   <span data-ttu-id="6ddb3-193">Руки следует воспроизводить дважды, в противном случае — до завершения жеста.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-193">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="6ddb3-194">Для того чтобы пользователь имел время для регистрации и просмотра жеста, необходимо дважды выполнить цикл.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-194">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="6ddb3-195">Стрелки должны появления и исчезновения между циклами.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-195">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="6ddb3-196">Если руки пользователя видны с помощью камер HL2, но пользователи не выполняют необходимое взаимодействие, они будут отображаться через 10 секунд.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-196">If user’s hands are visible by HL2 cameras but users are not doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="6ddb3-197">Если руки пользователя не видны в HL2 камерах, они будут отображаться через 5 секунд.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-197">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="6ddb3-198">Если руки пользователя заметно отправляются с помощью HL2 камер в середине анимации, анимация будет завершена и исчезать.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-198">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="6ddb3-199">Если вы включаете речь, мы рекомендуем, чтобы он соответствовал жесту руки.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-199">If you are including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="6ddb3-200">Если вы научились по крайней мере один раз, повторяйте жест только в том случае, если обнаружено, что пользователь зависает.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-200">If you have taught the hands at least once, only repeat the gesture if its detected that the user is stuck.</span></span>
*   <span data-ttu-id="6ddb3-201">Если конкретные положения пальца и руки являются критически важными, пользователи могут четко видеть эти особенности анимации.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-201">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="6ddb3-202">Попробуйте англинг в руки, чтобы наиболее важные части были четко видны.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-202">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="6ddb3-203">Если вы заметили искажения в руки, вам нужно переходить к параметрам качества Unity увеличить количество костей.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-203">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the amount of bones.</span></span> 
 <span data-ttu-id="6ddb3-204">Перейдите к параметру Изменить > проекта Unity > качество > другие > веса Blend.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-204">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="6ddb3-205">Убедитесь, что выбрано "четыре кости" для просмотра гладких соединений.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-205">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![Пример: расположение меню](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a><span data-ttu-id="6ddb3-207">Чего следует избегать</span><span class="sxs-lookup"><span data-stu-id="6ddb3-207">What to avoid</span></span>
* <span data-ttu-id="6ddb3-208">Масштабирование слишком больших стрелок</span><span class="sxs-lookup"><span data-stu-id="6ddb3-208">Scaling the Hands too large</span></span>
* <span data-ttu-id="6ddb3-209">поместив слишком близкое окно к пользователю</span><span class="sxs-lookup"><span data-stu-id="6ddb3-209">placing the Hands too close to the user</span></span>
* <span data-ttu-id="6ddb3-210">Руки следует научиться только один раз.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-210">Hands should only be taught once.</span></span> <span data-ttu-id="6ddb3-211">Чрезмерное обучение может привести к путанице и неправильной работе</span><span class="sxs-lookup"><span data-stu-id="6ddb3-211">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="6ddb3-212">Приведя его к Unity, скачайте последнюю версию МРТК здесь:https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="6ddb3-212">Bringing it into Unity, please download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="6ddb3-213">Материал: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="6ddb3-213">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="6ddb3-214">Сценарии. см. рекомендации по МРТК для <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">мртк</a></span><span class="sxs-lookup"><span data-stu-id="6ddb3-214">Scripts: Refer to MRTK guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="6ddb3-215">Параметр для каждого проекта</span><span class="sxs-lookup"><span data-stu-id="6ddb3-215">Per- project setting</span></span>
        *   <span data-ttu-id="6ddb3-216">Для сцены задано значение UWP: инструкции см. в [проекте настройки Unity](Configure-Unity-Project.md) для Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="6ddb3-216">Scene set to UWP: Instruction can be found on the [Configure Unity Project](Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="6ddb3-217">См. также</span><span class="sxs-lookup"><span data-stu-id="6ddb3-217">See also</span></span>
* [<span data-ttu-id="6ddb3-218">Принципы взаимодействия</span><span class="sxs-lookup"><span data-stu-id="6ddb3-218">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="6ddb3-219">Процесс создания ресурсов</span><span class="sxs-lookup"><span data-stu-id="6ddb3-219">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="6ddb3-220">Жесты</span><span class="sxs-lookup"><span data-stu-id="6ddb3-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="6ddb3-221">Установка инструментов</span><span class="sxs-lookup"><span data-stu-id="6ddb3-221">Install the Tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="6ddb3-222">Настройка проекта Unity</span><span class="sxs-lookup"><span data-stu-id="6ddb3-222">Configure Unity Project</span></span>](Configure-Unity-Project.md)
* [<span data-ttu-id="6ddb3-223">Обзор разработки в Unity</span><span class="sxs-lookup"><span data-stu-id="6ddb3-223">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="6ddb3-224">МРТК 101</span><span class="sxs-lookup"><span data-stu-id="6ddb3-224">MRTK 101</span></span>](mrtk-101.md)
