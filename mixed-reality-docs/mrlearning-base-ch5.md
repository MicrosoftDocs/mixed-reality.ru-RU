---
title: Учебники по началу работы — 6. Просмотр дополнительных параметров ввода
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: aaa02ce118fd051d94311e837b143affc96ff72b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554308"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="d3047-105">6. Изучение дополнительных параметров ввода</span><span class="sxs-lookup"><span data-stu-id="d3047-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="d3047-106">В этом учебнике вы узнаете о нескольких дополнительных параметрах ввода для HoloLens 2, включая использование речевых команд, жестов панорамирования и отслеживания глаз.</span><span class="sxs-lookup"><span data-stu-id="d3047-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="d3047-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="d3047-107">Objectives</span></span>

* <span data-ttu-id="d3047-108">Активация событий с помощью голосовых команд и ключевых слов</span><span class="sxs-lookup"><span data-stu-id="d3047-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="d3047-109">Использование отслеживаний руки для сдвига текстур и трехмерных объектов с помощью отслеживания руки</span><span class="sxs-lookup"><span data-stu-id="d3047-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="d3047-110">Использование возможностей отслеживания взгляда HoloLens 2 для выбора объектов</span><span class="sxs-lookup"><span data-stu-id="d3047-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="d3047-111">Включение голосовых команд</span><span class="sxs-lookup"><span data-stu-id="d3047-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="d3047-112">В этом разделе будет реализована Голосовая команда, позволяющая пользователю воспроизвести звук на объекте восьмиядерными.</span><span class="sxs-lookup"><span data-stu-id="d3047-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="d3047-113">Для этого вы создадите новую голосовую команду, а затем настроите событие, чтобы оно запустит нужное действие при произнесении ключевого слова Command речи.</span><span class="sxs-lookup"><span data-stu-id="d3047-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="d3047-114">Ниже приведены основные действия, которые необходимо выполнить для достижения этого результата.</span><span class="sxs-lookup"><span data-stu-id="d3047-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="d3047-115">Клонировать входной профиль системы по умолчанию</span><span class="sxs-lookup"><span data-stu-id="d3047-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="d3047-116">Клонирование профиля голосовых команд по умолчанию</span><span class="sxs-lookup"><span data-stu-id="d3047-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="d3047-117">Создать новую голосовую команду</span><span class="sxs-lookup"><span data-stu-id="d3047-117">Create a new speech command</span></span>
4. <span data-ttu-id="d3047-118">Добавление и настройка компонента обработчика речевого ввода (script)</span><span class="sxs-lookup"><span data-stu-id="d3047-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="d3047-119">Реализация события ответа для команды распознавания речи</span><span class="sxs-lookup"><span data-stu-id="d3047-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="d3047-120">1. клонировать входной системный профиль по умолчанию</span><span class="sxs-lookup"><span data-stu-id="d3047-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="d3047-121">В окне Иерархия выберите объект **микседреалититулкит** , а затем в окне инспектора выберите вкладку **Вход** и клонировать **DefaultHoloLens2InputSystemProfile** , чтобы заменить его собственным настраиваемым **системным профилем ввода**:</span><span class="sxs-lookup"><span data-stu-id="d3047-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="d3047-123">Напоминание о том, как клонировать профили МРТК, можно найти в статье [Настройка профилей набора средств для смешанной реальности](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .</span><span class="sxs-lookup"><span data-stu-id="d3047-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="d3047-124">2. клонирование профиля голосовых команд по умолчанию</span><span class="sxs-lookup"><span data-stu-id="d3047-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="d3047-125">Разверните раздел **распознавания речи** и клонировать **дефаултмикседреалитиспичкоммандспрофиле** , чтобы заменить его своим собственным настраиваемым **профилем голосовых команд**:</span><span class="sxs-lookup"><span data-stu-id="d3047-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="d3047-127">3. Создание новой команды речи</span><span class="sxs-lookup"><span data-stu-id="d3047-127">3. Create a new speech command</span></span>

<span data-ttu-id="d3047-128">В разделе **речевые команды** нажмите кнопку **+ Добавить новую голосовую** команду, чтобы добавить новую команду речи в нижнюю часть списка существующих речевых команд, а затем в поле **ключевое слово** введите подходящее слово или фразу, например **Воспроизведение музыки**:</span><span class="sxs-lookup"><span data-stu-id="d3047-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="d3047-130">Если у компьютера нет микрофона и вы хотите протестировать голосовую команду с помощью имитации в редакторе, можно назначить KeyCode команде распознавания речи, которая позволит активировать ее при нажатии соответствующей клавиши.</span><span class="sxs-lookup"><span data-stu-id="d3047-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="d3047-131">4. Добавление и настройка компонента обработчика речевого ввода (script)</span><span class="sxs-lookup"><span data-stu-id="d3047-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="d3047-132">В окне Иерархия выберите объект **восьмиядерными** и добавьте компонент **обработчика речевого ввода (script)** в объект восьмиядерными.</span><span class="sxs-lookup"><span data-stu-id="d3047-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="d3047-133">Установите флажок **является обязательным для фокуса** , чтобы пользователю не требовалось просматривать объект восьмиядерными, чтобы активировать голосовую команду:</span><span class="sxs-lookup"><span data-stu-id="d3047-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="d3047-135">5. Реализация события ответа для команды распознавания речи</span><span class="sxs-lookup"><span data-stu-id="d3047-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="d3047-136">В компоненте обработчика речевого ввода (скрипт) нажмите кнопку мелкий **+** , чтобы добавить элемент keyword в список ключевых слов:</span><span class="sxs-lookup"><span data-stu-id="d3047-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="d3047-138">Щелкните созданный **элемент 0** , чтобы развернуть его, а затем в раскрывающемся списке **ключевых слов** выберите ключевое слово **воспроизвести музыку** , созданное ранее:</span><span class="sxs-lookup"><span data-stu-id="d3047-138">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="d3047-140">Ключевые слова в раскрывающемся списке ключевых слов заполняются на основе ключевых слов, определенных в списке речевых команд в профиле голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="d3047-140">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="d3047-141">Создайте новое событие **Response ()** , настройте объект **восьмиядерными** для получения события, определите **аудиосаурце. плайонешот** в качестве действия, которое необходимо активировать, и назначьте подходящий звуковой клип полю **аудиоклипа** , например, MRTK_Gem аудиоклип:</span><span class="sxs-lookup"><span data-stu-id="d3047-141">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="d3047-143">Напоминание о том, как реализовать события и назначить аудиоклип, можно найти в разделе [Реализация событий On Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) .</span><span class="sxs-lookup"><span data-stu-id="d3047-143">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="d3047-144">Жест сдвига</span><span class="sxs-lookup"><span data-stu-id="d3047-144">The Pan Gesture</span></span>

<span data-ttu-id="d3047-145">Жест панорамирования удобен для прокрутки с помощью пальца или руки для прокрутки содержимого.</span><span class="sxs-lookup"><span data-stu-id="d3047-145">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="d3047-146">В этом примере вы сначала научитесь прокручивать 2D-пользовательский интерфейс, а затем разворачивать его, чтобы иметь возможность прокручивать коллекцию трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="d3047-146">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="d3047-147">Ниже приведены основные действия, которые необходимо выполнить для достижения этого результата.</span><span class="sxs-lookup"><span data-stu-id="d3047-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="d3047-148">Создать объект Quad, который можно использовать для панорамирования</span><span class="sxs-lookup"><span data-stu-id="d3047-148">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="d3047-149">Добавление компонента с сенсорным взаимодействием (script)</span><span class="sxs-lookup"><span data-stu-id="d3047-149">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="d3047-150">Добавление компонента "Масштаб" (скрипт) взаимодействия с руки</span><span class="sxs-lookup"><span data-stu-id="d3047-150">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="d3047-151">Добавить 2D-содержимое для прокрутки</span><span class="sxs-lookup"><span data-stu-id="d3047-151">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="d3047-152">Добавить трехмерное содержимое для прокрутки</span><span class="sxs-lookup"><span data-stu-id="d3047-152">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="d3047-153">Добавление компонента "переместить с помощью Pan" (скрипт)</span><span class="sxs-lookup"><span data-stu-id="d3047-153">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="d3047-154">Компонент перемещения с помощью элемента PAN (script) не является частью МРТК.</span><span class="sxs-lookup"><span data-stu-id="d3047-154">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="d3047-155">Он был предоставлен с ресурсами этого учебника.</span><span class="sxs-lookup"><span data-stu-id="d3047-155">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="d3047-156">1. Создайте объект Quad, который можно использовать для панорамирования.</span><span class="sxs-lookup"><span data-stu-id="d3047-156">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="d3047-157">В окне Иерархия щелкните правой кнопкой мыши пустую область и выберите **трехмерный объект** > « **четыре** », чтобы добавить в сцену четыре элемента.</span><span class="sxs-lookup"><span data-stu-id="d3047-157">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="d3047-158">Присвойте ему подходящее имя, например **панжестуре**, и поместите его в подходящее расположение, например X = 0, Y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="d3047-158">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="d3047-160">Напоминание о добавлении в сцену примитивов Unity, таких как объемные четыре, можно найти в инструкциях по [добавлению Куба к](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) сцене.</span><span class="sxs-lookup"><span data-stu-id="d3047-160">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="d3047-161">Как и при любом другом взаимодействии, для жеста сдвига также требуется объект, являющийся механизмом.</span><span class="sxs-lookup"><span data-stu-id="d3047-161">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="d3047-162">По умолчанию четырехъядерный объект имеет конфликты сетки.</span><span class="sxs-lookup"><span data-stu-id="d3047-162">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="d3047-163">Тем не менее, конфликты сетки не идеально подходят, так как это чрезвычайно тонкий.</span><span class="sxs-lookup"><span data-stu-id="d3047-163">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="d3047-164">Чтобы упростить взаимодействие пользователя с конфликтующим, мы заменили конфликтующую сетку с помощью блочного конфликта.</span><span class="sxs-lookup"><span data-stu-id="d3047-164">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="d3047-165">Выбрав объект Панжестуре, щелкните значок " **Параметры** " компонента " **конфликт сетки** " и выберите **удалить компонент** , чтобы удалить конфликтующую сетку:</span><span class="sxs-lookup"><span data-stu-id="d3047-165">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="d3047-167">В окне инспектора нажмите кнопку **Добавить компонент** , чтобы добавить **рамку**, а затем измените значение поля **Размер** отчасти от Z на 0,15, чтобы увеличить толщину окна "рамка".</span><span class="sxs-lookup"><span data-stu-id="d3047-167">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="d3047-169">2. Добавьте компонент с сенсорным взаимодействием (script).</span><span class="sxs-lookup"><span data-stu-id="d3047-169">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="d3047-170">Выбрав объект **панжестуре** , добавьте в объект панжестуре элемент с **сенсорным взаимодействием (script)** , а затем щелкните кнопки **исправить границы** и **центр исправлений** , чтобы обновить локальные свойства центра и границ близкого взаимодействия (скрипт), чтобы они соответствовали боксколлидер:</span><span class="sxs-lookup"><span data-stu-id="d3047-170">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="d3047-172">3. Добавление компонента "Масштаб" (скрипт) для взаимодействия с руки</span><span class="sxs-lookup"><span data-stu-id="d3047-172">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="d3047-173">Если объект **панжестуре** все еще выбран, добавьте компонент « **масштаб» (сценарий) руки** в объект панжестуре, а затем установите флажок « **Блокировка по горизонтали** », чтобы разрешить только вертикальную прокрутку:</span><span class="sxs-lookup"><span data-stu-id="d3047-173">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="d3047-175">4. Добавьте 2D-содержимое для прокрутки</span><span class="sxs-lookup"><span data-stu-id="d3047-175">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="d3047-176">На панели "проект" найдите материал **панконтент** , а затем щелкните его и перетащите в свойство "элемент **Material** объекта **панжестуре** ".</span><span class="sxs-lookup"><span data-stu-id="d3047-176">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="d3047-178">В окне инспектора разверните вновь добавленный компонент **панконтент** Material, а затем измените его **Мозаичное** значение Y на 0,5, чтобы оно соответствовало значению X, а плитки отображались в виде квадрата:</span><span class="sxs-lookup"><span data-stu-id="d3047-178">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="d3047-180">Если теперь вы вводите режим игры, можно протестировать 2D-содержимое с помощью жеста панорамирования в модели в редакторе:</span><span class="sxs-lookup"><span data-stu-id="d3047-180">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="d3047-182">5. Добавьте трехмерное содержимое для прокрутки</span><span class="sxs-lookup"><span data-stu-id="d3047-182">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="d3047-183">В окне Иерархия **Создайте четыре Куба** в качестве дочерних объектов объекта **панжестуре** и задайте для их **шкалы** преобразования значение X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="d3047-183">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="d3047-185">Для равномерного промежутка между кубами и экономии времени добавьте компонент **Коллекция объектов сетки (скрипт)** в родительский объект Cubes, т. е. объект **панжестуре** , и настройте коллекцию объектов Grid (скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d3047-185">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="d3047-186">Измените **число строк** на 1, чтобы все Кубы были согласованы в одной строке.</span><span class="sxs-lookup"><span data-stu-id="d3047-186">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="d3047-187">Измените **ширину ячейки** на 0,25, чтобы пропустить Кубы в строке</span><span class="sxs-lookup"><span data-stu-id="d3047-187">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="d3047-188">Затем нажмите кнопку **Update Collection (обновить коллекцию** ), чтобы применить новую конфигурацию:</span><span class="sxs-lookup"><span data-stu-id="d3047-188">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="d3047-190">6. Добавление компонента "переместить с помощью Pan" (скрипт)</span><span class="sxs-lookup"><span data-stu-id="d3047-190">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="d3047-191">В окне Иерархия выберите все **дочерние объекты куба**, а затем в окне инспектора нажмите кнопку **Добавить компонент** , чтобы добавить компонент " **переместить с помощью панорамы (скрипт)** " во все Кубы:</span><span class="sxs-lookup"><span data-stu-id="d3047-191">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="d3047-193">Напоминание о том, как выбрать несколько объектов в окне иерархии, условий использования можно найти в разделе [Добавление компонента обработчика манипуляций (script) ко всем](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) инструкциям по работе с объектами.</span><span class="sxs-lookup"><span data-stu-id="d3047-193">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="d3047-194">После выбора всех кубов щелкните и перетащите объект **панжестуре** в поле **источник входных данных Pan** :</span><span class="sxs-lookup"><span data-stu-id="d3047-194">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="d3047-196">Компонент "переместить с помощью панорамы" (скрипт) в каждом кубе прослушивает событие "сдвиг обновлена", отправленное компонентом Хандинтерактионпанзум (script), в объекте Панжестуре, который был назначен как источник входных данных Pan на шаге выше, и обновляет положение каждого куба. соответствующее.</span><span class="sxs-lookup"><span data-stu-id="d3047-196">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="d3047-197">В окне Иерархия выберите объект **панжестуре** , а затем в инспекторе снимите **флажок** для модуля подготовки к **просмотру сетки** , чтобы отключить компонент модуля подготовки к просмотру.</span><span class="sxs-lookup"><span data-stu-id="d3047-197">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="d3047-199">Если теперь вы вводите режим игры, можно протестировать трехмерное содержимое с помощью жеста панорамирования в модели в редакторе:</span><span class="sxs-lookup"><span data-stu-id="d3047-199">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="d3047-201">Отслеживание взгляда</span><span class="sxs-lookup"><span data-stu-id="d3047-201">Eye Tracking</span></span>

<span data-ttu-id="d3047-202">В этом разделе вы узнаете, как включить отслеживание взглядов в проекте.</span><span class="sxs-lookup"><span data-stu-id="d3047-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="d3047-203">В этом примере вы реализуете функции для того, чтобы каждый объект в 3DObjectCollection вращается медленно при просмотре взгляда пользователя, а также запускает эффект кратковременного сбоя, когда просматриваемый объект выбирается с помощью команды Air-TAP или речи.</span><span class="sxs-lookup"><span data-stu-id="d3047-203">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="d3047-204">Ниже приведены основные действия, которые необходимо выполнить для достижения этого результата.</span><span class="sxs-lookup"><span data-stu-id="d3047-204">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="d3047-205">Добавьте компонент цели отслеживания взгляда (script) для всех целевых объектов</span><span class="sxs-lookup"><span data-stu-id="d3047-205">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="d3047-206">Добавьте компонент учебника по отслеживанию взгляда (script) для всех целевых объектов</span><span class="sxs-lookup"><span data-stu-id="d3047-206">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="d3047-207">Реализовать событие While при просмотре целевого объекта</span><span class="sxs-lookup"><span data-stu-id="d3047-207">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="d3047-208">Реализовать выбранное событие</span><span class="sxs-lookup"><span data-stu-id="d3047-208">Implement the On Selected event</span></span>
5. <span data-ttu-id="d3047-209">Включение имитации отслеживания взгляда для имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="d3047-209">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="d3047-210">Включение ввода с помощью взгляда в возможности приложения проекта Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d3047-210">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="d3047-211">1. Добавьте целевой компонент отслеживания взгляда (script) для всех целевых объектов</span><span class="sxs-lookup"><span data-stu-id="d3047-211">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="d3047-212">В окне Иерархия разверните объект **3DObjectCollection** и выберите все **дочерние объекты**, а затем в окне инспектора нажмите кнопку **Добавить компонент** , чтобы добавить компонент **цели отслеживания взгляда (script)** в все дочерние объекты:</span><span class="sxs-lookup"><span data-stu-id="d3047-212">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="d3047-214">Выбрав все **дочерние объекты** , настройте компонент **цели отслеживания взгляда (script)** следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d3047-214">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="d3047-215">Изменить **выберите действие** для **выбора**, чтобы определить действие "Воздушный нажим" для этого объекта как SELECT</span><span class="sxs-lookup"><span data-stu-id="d3047-215">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="d3047-216">Развернуть **голос SELECT** и установить для списка команд голосового **формата** значение 1, а затем в списке новый элемент измените значение **элемента 0** на **SELECT**, чтобы определить действие команды речи для этого объекта в качестве SELECT.</span><span class="sxs-lookup"><span data-stu-id="d3047-216">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="d3047-218">2. Добавьте компонент учебника по отслеживанию взгляда (script) для всех целевых объектов</span><span class="sxs-lookup"><span data-stu-id="d3047-218">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="d3047-219">Выбрав все **дочерние объекты** , нажмите кнопку **Добавить компонент** , чтобы добавить компонент **учебника по отслеживанию взгляда (script)** для всех дочерних объектов:</span><span class="sxs-lookup"><span data-stu-id="d3047-219">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="d3047-221">Компонент цели отслеживания взгляда (script) не является частью МРТК.</span><span class="sxs-lookup"><span data-stu-id="d3047-221">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="d3047-222">Он был предоставлен с ресурсами этого учебника.</span><span class="sxs-lookup"><span data-stu-id="d3047-222">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="d3047-223">3. Реализуйте событие при просмотре целевого события</span><span class="sxs-lookup"><span data-stu-id="d3047-223">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="d3047-224">В окне Иерархия выберите объект **Мак** , а затем создайте новое событие **при просмотре целевого объекта ()** , настройте объект **Мак** для получения события и определите **эйетраккингтуториалдемо. ротатетаржет** в качестве действия для запуска:</span><span class="sxs-lookup"><span data-stu-id="d3047-224">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="d3047-226">**Повторите эти действия** для каждого дочернего объекта в 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="d3047-226">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="d3047-227">Напоминание о том, как реализовать события, можно найти в разделе [жесты отслеживания руки и инструкции по взаимодействию с управляемыми кнопками](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) .</span><span class="sxs-lookup"><span data-stu-id="d3047-227">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="d3047-228">4. Реализация выбранного события</span><span class="sxs-lookup"><span data-stu-id="d3047-228">4. Implement the On Selected event</span></span>

<span data-ttu-id="d3047-229">В окне Иерархия выберите объект **Мак** , а затем создайте новое событие **on Selected ()** , настройте объект **Мак** для получения события и определите **эйетраккингтуториалдемо. блиптаржет** в качестве действия для запуска:</span><span class="sxs-lookup"><span data-stu-id="d3047-229">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="d3047-231">**Повторите эти действия** для каждого дочернего объекта в 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="d3047-231">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="d3047-232">5. Включение имитации отслеживания взгляда для имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="d3047-232">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="d3047-233">В окне Иерархия выберите объект **микседреалититулкит** , затем в окне инспектора перейдите на вкладку **входные** данные, раскройте раздел **поставщики входных данных** , а затем — **службу моделирования ввода** и клонировать **Дефаултмикседреалитинпутсимулатионпрофиле** , чтобы заменить его собственным настраиваемым **профилем моделирования ввода**:</span><span class="sxs-lookup"><span data-stu-id="d3047-233">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="d3047-235">Напоминание о том, как клонировать профили МРТК, можно найти в статье [Настройка профилей набора средств для смешанной реальности](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .</span><span class="sxs-lookup"><span data-stu-id="d3047-235">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="d3047-236">В разделе **симуляция глаз** установите флажок **имитировать изменение расположения глаз** , чтобы включить симуляцию отслеживания глаз:</span><span class="sxs-lookup"><span data-stu-id="d3047-236">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="d3047-238">Если теперь вы вводите режим игры, вы можете протестировать прокрутку и кратковременного сбояные эффекты, которые вы реализовали, настроив представление таким образом, чтобы курсор затронул один из объектов и использовал команду взаимодействия руки или речи, чтобы выбрать объект:</span><span class="sxs-lookup"><span data-stu-id="d3047-238">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="d3047-240">Если вы не использовали DefaultHoloLens2ConfigurationProfile для клонирования настраиваемого профиля конфигурации МРТК, как описано в инструкциях по [настройке набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) , отслеживание взгляда может не быть включено в проекте и его необходимо будет включить.</span><span class="sxs-lookup"><span data-stu-id="d3047-240">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="d3047-241">Для этого можно обратиться к статье [Приступая к работе с отслеживанием взгляда в](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) инструкциях мртк.</span><span class="sxs-lookup"><span data-stu-id="d3047-241">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="d3047-242">6. Включение ввода с помощью взгляда в возможности приложения проекта Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d3047-242">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="d3047-243">Перед сборкой и развертыванием приложения из Visual Studio на устройстве необходимо включить входные данные в приложении проекта.</span><span class="sxs-lookup"><span data-stu-id="d3047-243">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="d3047-244">Для этого можно выполнить [Тестирование приложения Unity в инструкциях HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) .</span><span class="sxs-lookup"><span data-stu-id="d3047-244">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d3047-245">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d3047-245">Congratulations</span></span>

<span data-ttu-id="d3047-246">Вы успешно добавили базовые возможности отслеживания взгляда в приложение.</span><span class="sxs-lookup"><span data-stu-id="d3047-246">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="d3047-247">Эти действия только открывают целый мир новых возможностей, которые предоставляет отслеживание взгляда.</span><span class="sxs-lookup"><span data-stu-id="d3047-247">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="d3047-248">В этом учебнике вы также узнали о других дополнительных возможностях ввода, например о голосовых командах и жестах панорамирования.</span><span class="sxs-lookup"><span data-stu-id="d3047-248">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="d3047-249">Следующее занятие: 7. Создание примера приложения лунного модуля</span><span class="sxs-lookup"><span data-stu-id="d3047-249">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
