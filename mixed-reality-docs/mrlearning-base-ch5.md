---
title: Серия руководств по началу работы, часть 6. Изучение дополнительных входных параметров
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 9a19ad59e520a2743aafd954910f43c6f51d6c8a
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441861"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="50be3-105">6. Изучение дополнительных входных параметров</span><span class="sxs-lookup"><span data-stu-id="50be3-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="50be3-106">В этом руководстве мы рассмотрим несколько вариантов расширенного ввода для HoloLens 2, в том числе голосовые команды, жесты сдвига и отслеживание взгляда.</span><span class="sxs-lookup"><span data-stu-id="50be3-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="50be3-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="50be3-107">Objectives</span></span>

* <span data-ttu-id="50be3-108">Активировать события с помощью голосовых команд и ключевых слов.</span><span class="sxs-lookup"><span data-stu-id="50be3-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="50be3-109">Применить отслеживаемые руки для сдвига текстур и трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="50be3-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="50be3-110">Использовать функцию отслеживания взгляда в HoloLens 2 для выбора объектов.</span><span class="sxs-lookup"><span data-stu-id="50be3-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="50be3-111">Включение голосовых команд</span><span class="sxs-lookup"><span data-stu-id="50be3-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="50be3-112">В рамках этого раздела будет реализована речевая команда, которая позволяет пользователю воспроизвести звук на объекте Octa.</span><span class="sxs-lookup"><span data-stu-id="50be3-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="50be3-113">Для этого вы создадите новую речевую команду и настроите событие, которое запускает нужное действие при произнесении ключевого слова для этой команды.</span><span class="sxs-lookup"><span data-stu-id="50be3-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="50be3-114">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="50be3-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="50be3-115">Клонирование профиля по умолчанию для системы ввода.</span><span class="sxs-lookup"><span data-stu-id="50be3-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="50be3-116">Клонирование профиля по умолчанию для речевых команд.</span><span class="sxs-lookup"><span data-stu-id="50be3-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="50be3-117">Добавление новой речевой команды.</span><span class="sxs-lookup"><span data-stu-id="50be3-117">Create a new speech command</span></span>
4. <span data-ttu-id="50be3-118">Добавление и настройка компонента "Speech Input Handler (Script)" (Обработчик речевого ввода — скрипт).</span><span class="sxs-lookup"><span data-stu-id="50be3-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="50be3-119">Реализация события ответа для речевой команды.</span><span class="sxs-lookup"><span data-stu-id="50be3-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="50be3-120">1. Клонирование профиля по умолчанию для системы ввода</span><span class="sxs-lookup"><span data-stu-id="50be3-120">1. Clone the default Input System Profile</span></span>
<span data-ttu-id="50be3-121">В окне "Иерархия" выберите объект **MixedRealityToolkit**, затем в окне "Инспектор" выберите вкладку **Input** (Ввод) и клонируйте объект **DefaultHoloLens2InputSystemProfile**, чтобы заменить его собственным настраиваемым **профилем системы ввода**:</span><span class="sxs-lookup"><span data-stu-id="50be3-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="50be3-123">Если вы используете MRTK 2.4.0 или более поздней версии:</span><span class="sxs-lookup"><span data-stu-id="50be3-123">If you're using MRTK 2.4.0 or later:</span></span>
> * <span data-ttu-id="50be3-124">Выберите объект **MixedRealityToolkit** на вкладке Hierarchy (Иерархия), откройте вкладку **Input** (Вводные данные) в окне Inspector (Инспектор) и разверните раздел **Pointers** (Указатели).</span><span class="sxs-lookup"><span data-stu-id="50be3-124">Select the **MixedRealityToolkit** object from the Hierarchy tab, then click the **Input** tab in the Inspector window and expand the **Pointers** section.</span></span> 
> * <span data-ttu-id="50be3-125">Клонируйте профиль **DefaultMixedRealityInputPointerProfile** и замените его своим собственным настраиваемым профилем **Input Pointer Profile**.</span><span class="sxs-lookup"><span data-stu-id="50be3-125">Clone the **DefaultMixedRealityInputPointerProfile** and replace it with your own customizable **Input Pointer Profile**.</span></span>
> * <span data-ttu-id="50be3-126">Убедитесь, что для параметра **Is Eye Tracked Enabled** (Отслеживание глаз включено) установлено значение true в разделе **Gaze Settings** (Параметры отслеживания взгляда).</span><span class="sxs-lookup"><span data-stu-id="50be3-126">Check that **Is Eye Tracked Enabled** is true in the **Gaze Settings** section.</span></span> 

> [!TIP]
> <span data-ttu-id="50be3-127">Чтобы вспомнить, как правильно клонировать профили MRTK, воспользуйтесь инструкциями из раздела о [настройке Набора средств для смешанной реальности](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="50be3-127">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="50be3-128">2. Клонирование профиля по умолчанию для речевых команд</span><span class="sxs-lookup"><span data-stu-id="50be3-128">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="50be3-129">Разверните раздел **Speech** (Речь) и клонируйте **DefaultMixedRealitySpeechCommandsProfile**, чтобы заменить его собственным настраиваемым **профилем речевых команд**:</span><span class="sxs-lookup"><span data-stu-id="50be3-129">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="50be3-131">3. Добавление новой речевой команды</span><span class="sxs-lookup"><span data-stu-id="50be3-131">3. Create a new speech command</span></span>

<span data-ttu-id="50be3-132">В разделе **Speech Commands** (Речевые команды) щелкните **+ Add a New Speech Command** (Добавить голосовую команду), чтобы добавить новую речевую команду в конец списка существующих речевых команд, а затем в поле **Keyword** (Ключевое слово) введите подходящее слово или фразу, например **Play Music** (Воспроизвести музыку):</span><span class="sxs-lookup"><span data-stu-id="50be3-132">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="50be3-134">Если у компьютера нет микрофона и вы хотите протестировать речевую команду с помощью имитации в редакторе, можно назначить этой команде код клавиши, чтобы активировать команду нажатием соответствующей клавиши.</span><span class="sxs-lookup"><span data-stu-id="50be3-134">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="50be3-135">4. Добавление и настройка компонента "Speech Input Handler (Script)" (Обработчик речевого ввода — скрипт)</span><span class="sxs-lookup"><span data-stu-id="50be3-135">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="50be3-136">В окне "Иерархия" выберите объект **Octa** и добавьте в этот объект компонент **Speech Input Handler (Script)** (Обработчика речевого ввода — скрипт).</span><span class="sxs-lookup"><span data-stu-id="50be3-136">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="50be3-137">Снимите флажок **Is Focus Required** (Требуется фокус), чтобы пользователю не нужно было смотреть на объект Octa для активации этой речевой команды:</span><span class="sxs-lookup"><span data-stu-id="50be3-137">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="50be3-139">5. Реализация события ответа для речевой команды</span><span class="sxs-lookup"><span data-stu-id="50be3-139">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="50be3-140">В компоненте "Speech Input Handler (Script)" (Обработчик речевого ввода — скрипт) нажмите небольшую кнопку **+** , чтобы добавить элемент keyword (ключевое слово) в соответствующий список:</span><span class="sxs-lookup"><span data-stu-id="50be3-140">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="50be3-142">Щелкните только что созданный элемент **Element 0** (Элемент 0), чтобы развернуть его. Затем в раскрывающемся списке **Keyword** (Ключевое слово) выберите ранее созданное ключевое слово **Play Music** (Воспроизвести музыку):</span><span class="sxs-lookup"><span data-stu-id="50be3-142">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="50be3-144">Ключевые слова в раскрывающемся списке указываются из списка речевых команд в профиле речевых команд.</span><span class="sxs-lookup"><span data-stu-id="50be3-144">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="50be3-145">Создайте новое событие **Response ()** , настройте получение этого события в объекте **Octa**, определите **AudioSource.PlayOneShot** в качестве действия для активации и назначьте подходящий звуковой клип в поле **Audio Clip** (Звуковой клип), например, MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="50be3-145">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="50be3-147">В разделе о [реализации события On Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) вы можете освежить свои знания о реализации событий и назначении аудиоклипа.</span><span class="sxs-lookup"><span data-stu-id="50be3-147">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="50be3-148">Жест сдвига</span><span class="sxs-lookup"><span data-stu-id="50be3-148">The Pan Gesture</span></span>

<span data-ttu-id="50be3-149">Жест сдвига для прокрутки содержимого движением пальца или руки.</span><span class="sxs-lookup"><span data-stu-id="50be3-149">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="50be3-150">В рамках нашего примера вы сначала научитесь прокручивать двумерный пользовательский интерфейс, а затем дополните пример возможностью прокручивать коллекцию трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="50be3-150">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="50be3-151">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="50be3-151">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="50be3-152">Создание объекта Quad, который можно использовать для жеста сдвига.</span><span class="sxs-lookup"><span data-stu-id="50be3-152">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="50be3-153">Добавление компонента "Near Interaction Touchable (Script)" (Возможность касания при ближнем взаимодействии — скрипт).</span><span class="sxs-lookup"><span data-stu-id="50be3-153">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="50be3-154">Добавление компонента "Hand Interaction Pan Zoom (Script)" (Масштабирование сдвигом при взаимодействии рукой — скрипт).</span><span class="sxs-lookup"><span data-stu-id="50be3-154">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="50be3-155">Добавление двумерного содержимого для прокрутки.</span><span class="sxs-lookup"><span data-stu-id="50be3-155">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="50be3-156">Добавление трехмерного содержимого для прокрутки.</span><span class="sxs-lookup"><span data-stu-id="50be3-156">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="50be3-157">Добавление компонента "Move With Pan (Script)" (Смещение жестом сдвига — скрипт).</span><span class="sxs-lookup"><span data-stu-id="50be3-157">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="50be3-158">Компонент "Move With Pan (Script)" (Смещение жестом сдвига — скрипт) не входит в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="50be3-158">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="50be3-159">Он был предоставлен с активами для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="50be3-159">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="50be3-160">1. Создание объекта Quad, который можно использовать для жеста сдвига</span><span class="sxs-lookup"><span data-stu-id="50be3-160">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="50be3-161">Щелкните правой кнопкой мыши пустое место в окне "Иерархия" и выберите **Трехмерный объект** > **Quad**, чтобы добавить его в сцену.</span><span class="sxs-lookup"><span data-stu-id="50be3-161">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="50be3-162">Присвойте ему подходящее имя, например **PanGesture**, и разместите его в подходящем расположении, например с координатами X = 0, Y = –0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="50be3-162">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="50be3-164">В разделе о [добавлении куба в сцену](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) вы можете освежить свои знания о добавлении примитивов Unity.</span><span class="sxs-lookup"><span data-stu-id="50be3-164">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="50be3-165">Как и при любом другом взаимодействии, для жеста сдвига требуется коллайдер.</span><span class="sxs-lookup"><span data-stu-id="50be3-165">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="50be3-166">По умолчанию объект Quad имеет коллайдер сетки.</span><span class="sxs-lookup"><span data-stu-id="50be3-166">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="50be3-167">Этот вариант нам подходит плохо, так как коллайдер сетки очень тонкий.</span><span class="sxs-lookup"><span data-stu-id="50be3-167">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="50be3-168">Чтобы упростить взаимодействие пользователя с коллайдером, мы заменили коллайдер сетки блочным коллайдером.</span><span class="sxs-lookup"><span data-stu-id="50be3-168">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="50be3-169">Сохраняя выделение объекта PanGesture, щелкните значок **Параметры** компонента **Коллайдер сетки** и выберите команду **Удалить компонент**, чтобы удалить этот коллайдер сетки:</span><span class="sxs-lookup"><span data-stu-id="50be3-169">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="50be3-171">В окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить **блочный коллайдер**. Затем укажите для поля **Размер** значение Z = 0,15, чтобы увеличить толщину коллайдера.</span><span class="sxs-lookup"><span data-stu-id="50be3-171">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="50be3-173">2. Добавление компонента "Near Interaction Touchable (Script)" (Возможность касания при ближнем взаимодействии — скрипт)</span><span class="sxs-lookup"><span data-stu-id="50be3-173">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="50be3-174">Оставляя выделенным объект **PanGesture**, добавьте компонент **Near Interaction Touchable (Script)** (Возможность касания при ближнем взаимодействии — скрипт). Нажмите кнопки **Fix Bounds** (Зафиксировать границы) и **Fix Center** (Зафиксировать центр) для компонента "Near Interaction Touchable (Script)" (Возможность касания при ближнем взаимодействии — скрипт), чтобы он совпадал с объектом BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="50be3-174">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="50be3-176">3. Добавление компонента "Hand Interaction Pan Zoom (Script)" (Масштабирование сдвигом при взаимодействии рукой — скрипт)</span><span class="sxs-lookup"><span data-stu-id="50be3-176">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="50be3-177">Сохраняя выделение объекта **PanGesture**, добавьте в этот объект PanGesture компонент **Hand Interaction Pan Zoom** (Script)" (Масштабирование сдвигом при взаимодействии рукой — скрипт). Установите флажок **Lock Horizontal** (Блокировка по горизонтали), чтобы разрешить только вертикальную прокрутку:</span><span class="sxs-lookup"><span data-stu-id="50be3-177">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="50be3-179">4. Добавление двумерного содержимого для прокрутки</span><span class="sxs-lookup"><span data-stu-id="50be3-179">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="50be3-180">На панели "Проект" найдите материал **PanContent**, а затем щелкните его и перетащите в область свойства **Материал** для элемента 0 отрисовщика сетки для объекта **PanContent**:</span><span class="sxs-lookup"><span data-stu-id="50be3-180">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="50be3-182">В окне "Инспектор" разверните добавленный компонент материала **PanContent**. Затем укажите для параметра **Tiling** (Мозаичное заполнение) значение Y = 0,5, чтобы оно совпадало со значением X, то есть отображалась квадратная плитка:</span><span class="sxs-lookup"><span data-stu-id="50be3-182">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="50be3-184">Если теперь перейти в игровой режим, вы сможете протестировать прокрутку двумерного содержимого с помощью жеста панорамирования в имитации в редакторе:</span><span class="sxs-lookup"><span data-stu-id="50be3-184">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="50be3-186">5. Добавление трехмерного содержимого для прокрутки</span><span class="sxs-lookup"><span data-stu-id="50be3-186">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="50be3-187">В окне "Иерархия" **создайте четыре куба** в качестве дочерних объектов для объекта **PanGesture**. Присвойте значению преобразования **Масштаб** координаты X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="50be3-187">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="50be3-189">Чтобы равномерно распределить эти кубы и сэкономить некоторое время, добавьте компонент **Grid Object Collection (Script)** (Коллекция объектов сетки — скрипт) в родительский объект кубов, т. е. в объект **PanGesture**. Затем настройте эту коллекцию объектов сетки следующим образом:</span><span class="sxs-lookup"><span data-stu-id="50be3-189">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="50be3-190">Для параметра **Num Rows** (Число строк) установите значение 1, чтобы все кубы разместились в одном ряду.</span><span class="sxs-lookup"><span data-stu-id="50be3-190">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="50be3-191">Для параметра **Cell Width** (Ширина ячейки) установите значение 0,25, чтобы задать расстояние между кубами в одном ряду.</span><span class="sxs-lookup"><span data-stu-id="50be3-191">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="50be3-192">Нажмите кнопку **Update Collection** (Обновить коллекцию), чтобы применить новую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="50be3-192">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="50be3-194">6. Добавление компонента "Move With Pan (Script)" (Смещение жестом сдвига — скрипт)</span><span class="sxs-lookup"><span data-stu-id="50be3-194">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="50be3-195">В окне "Иерархия"выберите объект **Cube**, а затем в окне "Инспектор" с помощью кнопки **Добавить компонент** добавьте компонент **Move With Pan (Script)** (Смещение при сдвиге — скрипт) к каждому кубу.</span><span class="sxs-lookup"><span data-stu-id="50be3-195">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="50be3-197">В разделе о [добавлении компонента "Manipulation Handler (Script)" (Обработчик манипуляций — скрипт) ко всем объектам](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) вы можете освежить свои знания о выборе нескольких объектов в окне "Иерархия".</span><span class="sxs-lookup"><span data-stu-id="50be3-197">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="50be3-198">Выбрав все кубы, щелкните и перетащите объект **PanGesture** в поле **Pan Input Source** (Источник входа сдвига).</span><span class="sxs-lookup"><span data-stu-id="50be3-198">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="50be3-200">Компонент "Move With Pan (Script)" (Смещение при сдвиге — скрипт) в каждом кубе ожидает событие Pan Updated (Обновление сдвига) от компонента HandInteractionPanZoom (Script), размещенного в объекте PanGesture, который ранее был назначен как источник входных данных для сдвига, и соответствующим образом обновляет положение каждого куба.</span><span class="sxs-lookup"><span data-stu-id="50be3-200">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="50be3-201">В окне "Иерархия" выберите объект **PanGesture**, а затем в окне "Инспектор" **снимите** флажок **Mesh Renderer** (Отрисовщик сетки), чтобы отключить компонент отрисовщика сетки.</span><span class="sxs-lookup"><span data-stu-id="50be3-201">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="50be3-203">Если теперь перейти в игровой режим, вы сможете протестировать прокрутку трехмерного содержимого с помощью жеста панорамирования в имитации в редакторе:</span><span class="sxs-lookup"><span data-stu-id="50be3-203">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="50be3-205">Отслеживание взгляда</span><span class="sxs-lookup"><span data-stu-id="50be3-205">Eye Tracking</span></span>

<span data-ttu-id="50be3-206">Из этого раздела вы узнаете, как включить отслеживание взгляда в нашем демонстрационном проекте.</span><span class="sxs-lookup"><span data-stu-id="50be3-206">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="50be3-207">В рамках этого примера вы реализуете возможность медленно вращать каждый объект в коллекции 3DObjectCollection, когда на него смотрит пользователь. Кроме того, вы научитесь включать эффект звукового сигнала, когда просматриваемый объект выбирают с помощью действия касания или речевой команды.</span><span class="sxs-lookup"><span data-stu-id="50be3-207">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="50be3-208">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="50be3-208">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="50be3-209">Добавление компонента Eye Tracking Target (Script) (Целевой объект отслеживания взгляда — скрипт) в целевые объекты.</span><span class="sxs-lookup"><span data-stu-id="50be3-209">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="50be3-210">Добавление компонента Eye Tracking Tutorial Demo (Script) (Демонстрация отслеживания взгляда для руководства — скрипт) в целевые объекты.</span><span class="sxs-lookup"><span data-stu-id="50be3-210">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="50be3-211">Реализация события While Looking At Target.</span><span class="sxs-lookup"><span data-stu-id="50be3-211">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="50be3-212">Реализация события On Selected.</span><span class="sxs-lookup"><span data-stu-id="50be3-212">Implement the On Selected event</span></span>
5. <span data-ttu-id="50be3-213">Включение имитации отслеживания взгляда для имитации в редакторе.</span><span class="sxs-lookup"><span data-stu-id="50be3-213">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="50be3-214">Включение ввода с помощью взгляда в возможностях приложения проекта Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50be3-214">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="50be3-215">1. Добавление компонента Eye Tracking Target (Script) (Целевой объект отслеживания взгляда — скрипт) в целевые объекты</span><span class="sxs-lookup"><span data-stu-id="50be3-215">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="50be3-216">В окне "Иерархия" разверните объект **3DObjectCollection**. Выберите все его **дочерние объекты**. Затем в окне "Инспектор" с помощью кнопки **Добавить компонент** добавьте компонент **Eye Tracking Target (Script)** (Целевой объект отслеживания взгляда — скрипт) во все дочерние объекты:</span><span class="sxs-lookup"><span data-stu-id="50be3-216">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="50be3-218">Сохраняя выделение всех **дочерних объектов**, настройте компонент **Eye Tracking Target (Script)** (Целевой объект отслеживания взгляда — скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="50be3-218">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="50be3-219">Для параметра **Select Action** (Выберите действие) укажите значение **Select** (Выбор), чтобы определить действие "Выбор" при касании для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="50be3-219">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="50be3-220">Разверните раздел **Voice Select** (Голосовой выбор). Задайте для **размера** списка голосовых команд значение 1. Затем в новом списке измените **Element 0** (Элемент 0) на **Select** (Выбор), чтобы определить действие "Выбор" для речевой команды для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="50be3-220">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="50be3-222">2. Добавление компонента Eye Tracking Tutorial Demo (Script) (Демонстрация отслеживания взгляда для руководства — скрипт) в целевые объекты</span><span class="sxs-lookup"><span data-stu-id="50be3-222">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="50be3-223">Сохраняя выбранными все **дочерние объекты**, с помощью кнопки **Добавить компонент** добавьте компонент **Eye Tracking Tutorial Demo (Script)** (Демонстрация отслеживания взгляда для руководства — скрипт) во все дочерние объекты.</span><span class="sxs-lookup"><span data-stu-id="50be3-223">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="50be3-225">Компонент Eye Tracking Target (Script) (Целевой объект отслеживания взгляда — скрипт) не входит в состав MRTK.</span><span class="sxs-lookup"><span data-stu-id="50be3-225">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="50be3-226">Он был предоставлен с активами для этого руководства.</span><span class="sxs-lookup"><span data-stu-id="50be3-226">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="50be3-227">3. Реализация события While Looking At Target</span><span class="sxs-lookup"><span data-stu-id="50be3-227">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="50be3-228">В окне "Иерархия" выберите объект **Cheese**. Затем создайте новое событие **While Looking At Target ()** (При взгляде на целевой объект)ю Настройте получение этого события в объекте **Cheese** и определите **EyeTrackingTutorialDemo.RotateTarget** в качестве запускаемого действия:</span><span class="sxs-lookup"><span data-stu-id="50be3-228">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="50be3-230">**Повторно выполните** процесс для каждого из дочерних объектов коллекции 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="50be3-230">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="50be3-231">В разделе об [обработке жестов и нажатий активных кнопок с помощью средства отслеживания руки](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) вы можете освежить свои знания о реализации событий.</span><span class="sxs-lookup"><span data-stu-id="50be3-231">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="50be3-232">4. Реализация события On Selected</span><span class="sxs-lookup"><span data-stu-id="50be3-232">4. Implement the On Selected event</span></span>

<span data-ttu-id="50be3-233">В окне "Иерархия" выберите объект **Cheese**. Затем создайте событие **On Selected ()** (При выборе). Настройте получение этого события в объекте **Cheese** и определите **EyeTrackingTutorialDemo.BlipTarget** в качестве запускаемого действия:</span><span class="sxs-lookup"><span data-stu-id="50be3-233">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="50be3-235">**Повторно выполните** процесс для каждого из дочерних объектов коллекции 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="50be3-235">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="50be3-236">5. Включение имитации отслеживания взгляда для имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="50be3-236">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="50be3-237">В окне "Иерархия" выберите объект **MixedRealityToolkit**. Затем в окне "Инспектор" выберите вкладку **Input** (Ввод). Разверните раздел **Input Data Providers** (Поставщики данных ввода) и раздел **Input Simulation Service** (Служба имитации ввода). Клонируйте объект **DefaultMixedRealityInputSimulationProfile**, чтобы заменить его собственным настраиваемым **профилем имитации ввода**:</span><span class="sxs-lookup"><span data-stu-id="50be3-237">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="50be3-239">Чтобы вспомнить, как правильно клонировать профили MRTK, воспользуйтесь инструкциями из раздела о [настройке Набора средств для смешанной реальности](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="50be3-239">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="50be3-240">В разделе **Eye Simulation** (Имитация взгляда) установите флажок **Simulate Eye Position** (Имитировать положение глаз), чтобы включить имитацию отслеживания глаз:</span><span class="sxs-lookup"><span data-stu-id="50be3-240">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="50be3-242">Если теперь вы войдете в игровой режим, то сможете протестировать настроенные эффекты вращения и звукового сигнала, взглядом перемещая курсор к одному из объектов и используя взаимодействие рукой или речевую команду, чтобы выбрать объект:</span><span class="sxs-lookup"><span data-stu-id="50be3-242">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="50be3-244">Если вы не использовали DefaultHoloLens2ConfigurationProfile для клонирования настраиваемого профиля конфигурации МRТК, как описано в разделе о [настройке Набора средств для смешанной реальности](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), отслеживание глаз может не работать в проекте и его придется включить.</span><span class="sxs-lookup"><span data-stu-id="50be3-244">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="50be3-245">Дополнительные сведения см. в статье [о начале работы с отслеживанием взгляда в МRТК](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html).</span><span class="sxs-lookup"><span data-stu-id="50be3-245">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="50be3-246">6. Включение ввода с помощью взгляда в возможностях приложения проекта Visual Studio</span><span class="sxs-lookup"><span data-stu-id="50be3-246">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="50be3-247">Прежде чем компилировать и развертывать приложение из Visual Studio на устройстве, необходимо включить в приложении проекта ввод с помощью взгляда.</span><span class="sxs-lookup"><span data-stu-id="50be3-247">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="50be3-248">Дополнительные сведения см. в разделе о [тестировании приложения Unity на устройстве HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="50be3-248">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="50be3-249">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="50be3-249">Congratulations</span></span>

<span data-ttu-id="50be3-250">Вы успешно добавили в приложение базовые возможности отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="50be3-250">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="50be3-251">Эти действия только открывают целый мир новых возможностей, которые предоставляет отслеживание взгляда.</span><span class="sxs-lookup"><span data-stu-id="50be3-251">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="50be3-252">Кроме того, из этого руководстве вы узнали о других возможностях расширенного ввода, таких как голосовые команды и жесты сдвига.</span><span class="sxs-lookup"><span data-stu-id="50be3-252">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="50be3-253">Следующий урок. 7. Создание примера приложения лунного модуля</span><span class="sxs-lookup"><span data-stu-id="50be3-253">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
