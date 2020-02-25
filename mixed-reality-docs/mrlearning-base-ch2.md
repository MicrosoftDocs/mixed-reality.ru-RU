---
title: Учебники по началу работы — 3. Создание пользовательского интерфейса и настройка набора средств для смешанной реальности
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: f1d042150d1c81940e672b174c6c02ac71e05883
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555053"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="ae51c-105">3. Создание пользовательского интерфейса и настройка набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="ae51c-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="ae51c-106">В предыдущем учебном курсе вы узнали о некоторых возможностях набора средств Mixed Reality (МРТК), которые необходимо предоставить, запустив первое приложение для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ae51c-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="ae51c-107">В этом учебнике вы узнаете, как создавать и упорядочивать кнопки вместе с панелями текста пользовательского интерфейса и использовать взаимодействие по умолчанию (Touch) для взаимодействия с каждой кнопкой.</span><span class="sxs-lookup"><span data-stu-id="ae51c-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="ae51c-108">Кроме того, вы освоите добавление простых действий и эффектов, например изменение размера, звука и цвета для объектов.</span><span class="sxs-lookup"><span data-stu-id="ae51c-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="ae51c-109">Этот модуль предоставит основные понятия об изменении профилей МРТК, начиная с отключения визуализации сетки [пространственного сопоставления](spatial-mapping.md) .</span><span class="sxs-lookup"><span data-stu-id="ae51c-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="ae51c-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="ae51c-110">Objectives</span></span>

* <span data-ttu-id="ae51c-111">Настройка профилей набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="ae51c-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="ae51c-112">Взаимодействие с голограммами с помощью элементов пользовательского интерфейса и кнопок</span><span class="sxs-lookup"><span data-stu-id="ae51c-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="ae51c-113">Базовый ввод данных и взаимодействие с помощью средства отслеживания руки</span><span class="sxs-lookup"><span data-stu-id="ae51c-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="ae51c-114">Настройка профилей набора средств для смешанной реальности (изменение параметров отображения сведений о пространственном состоянии)</span><span class="sxs-lookup"><span data-stu-id="ae51c-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="ae51c-115">В этом разделе вы узнаете, как настроить и настроить профили МРТК по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ae51c-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="ae51c-116">В этом конкретном примере показано, как скрыть сетку пространственной осведомленности, изменив параметры наблюдателя пространственной сетки.</span><span class="sxs-lookup"><span data-stu-id="ae51c-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="ae51c-117">Однако вы можете следовать тем же принципам для настройки любых параметров или значений в профилях МРТК.</span><span class="sxs-lookup"><span data-stu-id="ae51c-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="ae51c-118">Ниже приведены основные шаги, которые необходимо выполнить для скрытия сетки пространственных сведений.</span><span class="sxs-lookup"><span data-stu-id="ae51c-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="ae51c-119">Клонировать профиль конфигурации по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ae51c-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="ae51c-120">Включение системы распознавания пространственных</span><span class="sxs-lookup"><span data-stu-id="ae51c-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="ae51c-121">Клонировать профиль системы поддержки пространственного расположения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ae51c-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="ae51c-122">Клонирование профиля наблюдателя сетки по умолчанию для пространственного отслеживания</span><span class="sxs-lookup"><span data-stu-id="ae51c-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="ae51c-123">Изменение видимости сетки пространственного отслеживания</span><span class="sxs-lookup"><span data-stu-id="ae51c-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="ae51c-124">По умолчанию профили MRTK недоступны для редактирования.</span><span class="sxs-lookup"><span data-stu-id="ae51c-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="ae51c-125">Это шаблоны профилей по умолчанию, которые необходимо клонировать, прежде чем их можно будет редактировать.</span><span class="sxs-lookup"><span data-stu-id="ae51c-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="ae51c-126">Существует несколько вложенных слоев профилей.</span><span class="sxs-lookup"><span data-stu-id="ae51c-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="ae51c-127">Таким образом, при настройке одного или нескольких параметров часто копируются и редактируются несколько профилей.</span><span class="sxs-lookup"><span data-stu-id="ae51c-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="ae51c-128">1. клонирование профиля конфигурации по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ae51c-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="ae51c-129">Профиль конфигурации является профилем верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="ae51c-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="ae51c-130">Следовательно, чтобы иметь возможность изменять любые другие профили, сначала необходимо клонировать профиль конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ae51c-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="ae51c-131">Выбрав объект **микседреалититулкит** в окне Иерархия, в окне инспектора измените **профиль конфигурации** набора средств Mixed Reality на **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="ae51c-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="ae51c-133">Выбрав объект **микседреалититулкит** , в окне инспектора нажмите кнопку **Копировать & настроить** , чтобы открыть окно Профиль клона:</span><span class="sxs-lookup"><span data-stu-id="ae51c-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="ae51c-135">В окне Профиль клона нажмите кнопку **клонировать** , чтобы создать редактируемую копию **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="ae51c-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="ae51c-137">Созданный профиль конфигурации теперь назначается в качестве профиля конфигурации для сцены:</span><span class="sxs-lookup"><span data-stu-id="ae51c-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="ae51c-139">В меню Unity выберите **файл** > **сохранить** , чтобы сохранить сцену.</span><span class="sxs-lookup"><span data-stu-id="ae51c-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="ae51c-140">Не забудьте сохранить работу в рамках этого руководства.</span><span class="sxs-lookup"><span data-stu-id="ae51c-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="ae51c-141">2. Включение системы распознавания пространственных сведений</span><span class="sxs-lookup"><span data-stu-id="ae51c-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="ae51c-142">Если объект **микседреалититулкит** все еще выбран в окне "иерархия", в окне инспектора перейдите на вкладку **пространственное распознавание** и установите флажок **включить систему пространственной осведомленности** :</span><span class="sxs-lookup"><span data-stu-id="ae51c-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="ae51c-144">3. Клонирование системного профиля сведений о пространственном распознавании по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ae51c-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="ae51c-145">На вкладке **пространственное распознавание** нажмите кнопку **клонировать** , чтобы открыть окно Профиль клона:</span><span class="sxs-lookup"><span data-stu-id="ae51c-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="ae51c-147">В окне Профиль клона нажмите кнопку **клонировать** , чтобы создать редактируемую копию **дефаултмикседреалитиспатиалаваренесссистемпрофиле**:</span><span class="sxs-lookup"><span data-stu-id="ae51c-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="ae51c-149">Вновь созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:</span><span class="sxs-lookup"><span data-stu-id="ae51c-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="ae51c-151">4. клонирование профиля наблюдателя сетки по умолчанию для пространственного отслеживания</span><span class="sxs-lookup"><span data-stu-id="ae51c-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="ae51c-152">Если вкладка " **пространственное распознавание** " все еще выбрана, разверните раздел **наблюдатель пространственной сетки Windows Mixed Reality** , а затем нажмите кнопку **клонировать** , чтобы открыть окно Профиль клона:</span><span class="sxs-lookup"><span data-stu-id="ae51c-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="ae51c-154">В окне Профиль клона нажмите кнопку **клонировать** , чтобы создать редактируемую копию **дефаултмикседреалитиспатиалаваренессмешобсерверпрофиле**:</span><span class="sxs-lookup"><span data-stu-id="ae51c-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="ae51c-156">Вновь созданный профиль наблюдателя сетки для пространственного отслеживания автоматически назначается системному профилю пространственного отслеживания:</span><span class="sxs-lookup"><span data-stu-id="ae51c-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="ae51c-158">5. изменение видимости сетки пространственного отслеживания</span><span class="sxs-lookup"><span data-stu-id="ae51c-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="ae51c-159">В **параметрах наблюдателя пространственной сетки**измените **параметр отображения** на **перекрытия** , чтобы сетка пространственных сопоставлений стала невидимой, пока все еще функционирует:</span><span class="sxs-lookup"><span data-stu-id="ae51c-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="ae51c-161">Хотя сетка пространственных сопоставлений не видна, она по-прежнему существует и работает.</span><span class="sxs-lookup"><span data-stu-id="ae51c-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="ae51c-162">Например, все голограммы в сетке пространственного сопоставления, такие как голограмма за физической стеной, не будут видны.</span><span class="sxs-lookup"><span data-stu-id="ae51c-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="ae51c-163">Вы только что узнали, как изменить параметр в профиле MRTK.</span><span class="sxs-lookup"><span data-stu-id="ae51c-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="ae51c-164">Как видите, для настройки параметров МРТК сначала необходимо создать копии профилей по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ae51c-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="ae51c-165">Так как профили по умолчанию недоступны для редактирования, они всегда будут иметь в качестве ссылки, если нужно вернуться к параметрам по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ae51c-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="ae51c-166">Дополнительные сведения о профилях МРТК и их архитектуре см. в [руководстве по настройке профиля набора средств для смешанной реальности](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) на [портале документации мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="ae51c-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="ae51c-167">Жесты отслеживания и взаимодействующие кнопки</span><span class="sxs-lookup"><span data-stu-id="ae51c-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="ae51c-168">В этом разделе вы узнаете, как использовать отслеживание вручную для нажатия кнопки и запуска событий, чтобы вызвать действие при нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="ae51c-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="ae51c-169">В этом конкретном примере показано, как изменить цвет куба при нажатии кнопки и вернуть его к исходному цвету при отпускании кнопки.</span><span class="sxs-lookup"><span data-stu-id="ae51c-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="ae51c-170">Однако вы можете следовать тем же принципам для создания других событий.</span><span class="sxs-lookup"><span data-stu-id="ae51c-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="ae51c-171">Ниже приведены основные действия, которые необходимо выполнить для изменения цвета Куба.</span><span class="sxs-lookup"><span data-stu-id="ae51c-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="ae51c-172">Добавление нажатой кнопки prefab в сцену</span><span class="sxs-lookup"><span data-stu-id="ae51c-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="ae51c-173">Добавление Куба в сцену</span><span class="sxs-lookup"><span data-stu-id="ae51c-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="ae51c-174">Настройка типа событий Интерактаблеонпрессрецеивер</span><span class="sxs-lookup"><span data-stu-id="ae51c-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="ae51c-175">Настройка куба для получения события "при нажатии"</span><span class="sxs-lookup"><span data-stu-id="ae51c-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="ae51c-176">Определение действия, запускаемого событием при нажатии кнопки</span><span class="sxs-lookup"><span data-stu-id="ae51c-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="ae51c-177">Настройка куба для получения события "при выпуске"</span><span class="sxs-lookup"><span data-stu-id="ae51c-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="ae51c-178">Определение действия, запускаемого событием выпуска</span><span class="sxs-lookup"><span data-stu-id="ae51c-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="ae51c-179">Тестирование кнопки с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="ae51c-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="ae51c-180">1. Добавление в сцену нажатой кнопки prefab</span><span class="sxs-lookup"><span data-stu-id="ae51c-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="ae51c-181"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> — это предварительно настроенный GameObject, хранящийся в качестве ресурса Unity, который можно повторно использовать во всем проекте.</span><span class="sxs-lookup"><span data-stu-id="ae51c-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="ae51c-182">В **окне проекта**найдите **PressableButtonHoloLens2** , чтобы найти prefab, который будет использоваться в этом примере:</span><span class="sxs-lookup"><span data-stu-id="ae51c-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="ae51c-184">В результатах **поиска** выберите **PressableButtonHoloLens2** prefab и **перетащите** его в окно **Иерархия** , чтобы добавить его в сцену:</span><span class="sxs-lookup"><span data-stu-id="ae51c-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="ae51c-186">Чтобы отобразить сцену, как показано на рисунке ниже, дважды щелкните объект PressableButtonHoloLens2 в окне "иерархия", чтобы перевести его в фокус, а затем используйте <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">сцену гизмо</a>, расположенную в правом верхнем углу окна сцены, чтобы настроить угол обзора на прямую ось Z.</span><span class="sxs-lookup"><span data-stu-id="ae51c-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="ae51c-187">Если объект **PressableButtonHoloLens2** все еще выбран, в окне **инспектора** :</span><span class="sxs-lookup"><span data-stu-id="ae51c-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="ae51c-188">Измените **положение** преобразования, чтобы оно расположиться перед камерой, которое позиционируется в начале, например x = 0, y = 0, и z = 0,5</span><span class="sxs-lookup"><span data-stu-id="ae51c-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="ae51c-190">Как правило, 1 единица позиций в Unity примерно эквивалентна одному измерению в физическом мире.</span><span class="sxs-lookup"><span data-stu-id="ae51c-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="ae51c-191">Однако существуют исключения, например, если объекты являются дочерними объектами масштабируемых объектов.</span><span class="sxs-lookup"><span data-stu-id="ae51c-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="ae51c-192">2. Добавление Куба в сцену</span><span class="sxs-lookup"><span data-stu-id="ae51c-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="ae51c-193">Щелкните правой кнопкой мыши пустое место в окне иерархии и выберите пункт **3D Object** > **куб** , чтобы добавить куб в сцену:</span><span class="sxs-lookup"><span data-stu-id="ae51c-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="ae51c-195">Выбрав объект **куба** , в окне **инспектора** :</span><span class="sxs-lookup"><span data-stu-id="ae51c-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="ae51c-196">Измените свое **Расположение** преобразования, чтобы оно находилось рядом с нажатой кнопкой, но не пересекается с ней, например x = 0, y = 0,04 и z = 0,5</span><span class="sxs-lookup"><span data-stu-id="ae51c-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="ae51c-197">Измените **масштаб** преобразования на подходящий размер, например x = 0,02, y = 0,02, и z = 0,02.</span><span class="sxs-lookup"><span data-stu-id="ae51c-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="ae51c-199">3. Настройка типа событий Интерактаблеонпрессрецеивер</span><span class="sxs-lookup"><span data-stu-id="ae51c-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="ae51c-200">В окне Иерархия выберите объект **PressableButtonHoloLens2** , а затем в **меню "гамбургер**" окна **инспектора** выберите **Свернуть все компоненты** , чтобы получить общие сведения о всех компонентах этого объекта:</span><span class="sxs-lookup"><span data-stu-id="ae51c-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="ae51c-202">Разверните компонент " **взаимодействие (скрипт)** ", а затем найдите и разверните раздел **события** > **получателей** :</span><span class="sxs-lookup"><span data-stu-id="ae51c-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="ae51c-204">Нажмите кнопку **Добавить событие** , чтобы создать приемник событий для приемника событий типа **интерактаблеонпрессрецеивер**:</span><span class="sxs-lookup"><span data-stu-id="ae51c-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="ae51c-206">Тип приемника событий с именем Интерактаблеонпрессрецеивер позволяет кнопке реагировать на событие нажатия, когда прослеживание руки нажимает кнопку.</span><span class="sxs-lookup"><span data-stu-id="ae51c-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="ae51c-207">Для вновь созданного приемника событий измените **Фильтр взаимодействия** на **NEAR и Far**:</span><span class="sxs-lookup"><span data-stu-id="ae51c-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="ae51c-209">4. Настройка куба для получения события "при нажатии"</span><span class="sxs-lookup"><span data-stu-id="ae51c-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="ae51c-210">В окне Иерархия **щелкните и перетащите** **куб** в поле объект **Свойства события** для события **при нажатии ()** , чтобы назначить куб в качестве получателя события On Press ():</span><span class="sxs-lookup"><span data-stu-id="ae51c-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="ae51c-212">5. Определение действия, запускаемого событием при нажатии кнопки</span><span class="sxs-lookup"><span data-stu-id="ae51c-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="ae51c-213">Щелкните раскрывающийся список действий, в данный момент не имеющий **функции**, а затем выберите **мешрендерер** > **материальный материал** , чтобы изменить свойство материала Куба при срабатывании события On Press ():</span><span class="sxs-lookup"><span data-stu-id="ae51c-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="ae51c-215">Щелкните маленький значок **круга** рядом с полем "материал" (в данный момент заполняется " **нет")** , чтобы открыть окно "Выбор материала":</span><span class="sxs-lookup"><span data-stu-id="ae51c-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="ae51c-217">В окне Выбор материала **найдите** **MRTK_Standard** и выберите подходящий материал, например **MRTK_Standard_Cyan** так, чтобы цвет Куба был изменен на голубой при нажатии кнопки:</span><span class="sxs-lookup"><span data-stu-id="ae51c-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="ae51c-219">6. Настройка куба для получения события "при выпуске"</span><span class="sxs-lookup"><span data-stu-id="ae51c-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="ae51c-220">**Повторить** Шаг 4 для события On Release для назначения **куба** в качестве получателя события **On Release ()** .</span><span class="sxs-lookup"><span data-stu-id="ae51c-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="ae51c-221">7. Определение действия, запускаемого событием выпуска</span><span class="sxs-lookup"><span data-stu-id="ae51c-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="ae51c-222">**Повторить** Шаг 5 для события On Release, но выберите **MRTK_Standard_LightGray** материал, чтобы цвет Куба возвращался к исходному светло-серому цвету при отпускании кнопки:</span><span class="sxs-lookup"><span data-stu-id="ae51c-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="ae51c-224">8. Тестирование кнопки с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="ae51c-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="ae51c-225">Нажмите кнопку " **Воспроизведение** ", чтобы перейти в режим игры и использовать имитацию ввода в редакторе для проверки вновь настроенной кнопки.</span><span class="sxs-lookup"><span data-stu-id="ae51c-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="ae51c-226">Кнопка не нажата (пробел + колесо прокрутки мыши назад):</span><span class="sxs-lookup"><span data-stu-id="ae51c-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="ae51c-228">Нажата кнопка (пробел + колесо прокрутки мыши вперед):</span><span class="sxs-lookup"><span data-stu-id="ae51c-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="ae51c-230">Чтобы узнать, как использовать имитацию входных данных в редакторе, можно обратиться к разделу [Использование имитации входных данных в редакторе, чтобы протестировать руководство по монтажному кадру](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) на [портале документации мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="ae51c-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="ae51c-231">Создание панели кнопок с помощью коллекции объектов сетки MRTK</span><span class="sxs-lookup"><span data-stu-id="ae51c-231">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="ae51c-232">В этом разделе вы узнаете, как автоматически выровняйте несколько кнопок в удобном пользовательском интерфейсе с помощью средства сбора объектов сетки МРТК.</span><span class="sxs-lookup"><span data-stu-id="ae51c-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s Grid Object Collection tool.</span></span>

<span data-ttu-id="ae51c-233">В этом конкретном примере показано, как создать панель с пятью кнопками по горизонтали.</span><span class="sxs-lookup"><span data-stu-id="ae51c-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="ae51c-234">Однако вы можете следовать тем же принципам для создания других макетов.</span><span class="sxs-lookup"><span data-stu-id="ae51c-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="ae51c-235">Ниже приведены основные действия, которые необходимо выполнить для достижения этого результата.</span><span class="sxs-lookup"><span data-stu-id="ae51c-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ae51c-236">Родительские объекты Button для родительского объекта</span><span class="sxs-lookup"><span data-stu-id="ae51c-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="ae51c-237">Добавление и настройка компонента "Коллекция объектов сетки" (скрипт)</span><span class="sxs-lookup"><span data-stu-id="ae51c-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="ae51c-238">Тестирование кнопок с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="ae51c-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="ae51c-239">1. родительские объекты кнопки для родительского объекта</span><span class="sxs-lookup"><span data-stu-id="ae51c-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="ae51c-240">Щелкните правой кнопкой мыши пустое место в окне иерархии и выберите **создать пустое**:</span><span class="sxs-lookup"><span data-stu-id="ae51c-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="ae51c-242">Щелкните правой кнопкой мыши созданный объект, выберите **Переименовать**и присвойте ему подходящее имя, например **буттонколлектион**:</span><span class="sxs-lookup"><span data-stu-id="ae51c-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="ae51c-244">Выберите объект **PressableButtonHoloLens2** и **перетащите** его поверх объекта **буттонколлектион** , чтобы сделать его дочерним по отношению к объекту буттонколлектион:</span><span class="sxs-lookup"><span data-stu-id="ae51c-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="ae51c-246">Щелкните правой кнопкой мыши объект **PressableButtonHoloLens2** и выберите пункт **дублировать** , чтобы создать его копию:</span><span class="sxs-lookup"><span data-stu-id="ae51c-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="ae51c-248">**Повторите** этот шаг четыре раза, пока не получите пять объектов PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="ae51c-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="ae51c-249">2. Добавление и настройка компонента "Коллекция объектов сетки" (скрипт)</span><span class="sxs-lookup"><span data-stu-id="ae51c-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="ae51c-250">Выбрав объект Буттонколлектион в окне Иерархия, в окне инспектора нажмите кнопку **Добавить компонент** , затем найдите и выберите **Коллекция объектов сетки** , чтобы добавить компонент коллекции объектов Grid (скрипт) в объект буттонколлектион:</span><span class="sxs-lookup"><span data-stu-id="ae51c-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="ae51c-252">Настройте коллекцию объектов Grid (скрипт) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ae51c-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="ae51c-253">Измените **число строк** на 1, чтобы все кнопки были высвоены по одной строке.</span><span class="sxs-lookup"><span data-stu-id="ae51c-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="ae51c-254">Измените **ширину ячейки** на 0,05, чтобы пропустить кнопки в строке</span><span class="sxs-lookup"><span data-stu-id="ae51c-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="ae51c-255">Затем нажмите кнопку **Update Collection (обновить коллекцию** ), чтобы применить новую конфигурацию:</span><span class="sxs-lookup"><span data-stu-id="ae51c-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="ae51c-257">Изменения конфигурации, которые вы только что заменили, представляют минимальные изменения, необходимые для достижения цели размещения кнопок в одной строке.</span><span class="sxs-lookup"><span data-stu-id="ae51c-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="ae51c-258">Однако в будущих проектах в зависимости от таких факторов, как, например, ориентация родительского и дочернего объектов, может потребоваться настроить другие параметры, такие как, например, тип ориентации.</span><span class="sxs-lookup"><span data-stu-id="ae51c-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="ae51c-259">Дополнительные сведения о коллекции объектов Grid МРТК см. в руководстве по созданию [сценариев коллекции объектов](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) на [портале документации мртк](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="ae51c-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="ae51c-260">Если объект Буттонколлектион все еще выбран в окне "иерархия", в окне инспектора измените **положение** преобразования объекта буттонколлектион так, чтобы его дочерние объекты кнопок были расположены перед камерой, расположенной в источнике, например x = 0, y = 0, и z = 0,5:</span><span class="sxs-lookup"><span data-stu-id="ae51c-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="ae51c-262">Когда вы впервые добавили prefab PressableButtonHoloLens2 в сцену в [жестах отслеживания руки и в разделе "взаимодействующие кнопки](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) " выше, вы размещаете его перед камерой.</span><span class="sxs-lookup"><span data-stu-id="ae51c-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="ae51c-263">Однако, поскольку коллекция объектов сетки управляет положением непосредственных дочерних объектов, значение координаты Z для дочерних объектов PressableButtonHoloLens2 сбрасывается в 0 в соответствии с расстоянием по умолчанию для коллекции объектов сетки от родительского значения 0.</span><span class="sxs-lookup"><span data-stu-id="ae51c-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="ae51c-264">Таким образом, и для того, чтобы упорядочить иерархические отношения «родители-потомки», именно поэтому мы перенесли положение родительского объекта Буттонколлектион вперед вместо настройки расстояния от родительского значения, чтобы переместить дочерние объекты PressableButtonHoloLens2 вперед.</span><span class="sxs-lookup"><span data-stu-id="ae51c-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="ae51c-265">3. Тестирование кнопок с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="ae51c-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="ae51c-266">Нажмите кнопку "Воспроизведение", чтобы перейти в режим игры и использовать модель входа в редакторе, чтобы проверить каждую из кнопок в созданной панели кнопок.</span><span class="sxs-lookup"><span data-stu-id="ae51c-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="ae51c-268">В настоящее время при нажатии любой из пяти кнопок Цвет Куба меняется на голубой.</span><span class="sxs-lookup"><span data-stu-id="ae51c-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="ae51c-269">Чтобы сделать интерес более интересным, используйте то, что вы только научитесь настраивать для каждой кнопки, чтобы изменить цвет куба на другой.</span><span class="sxs-lookup"><span data-stu-id="ae51c-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="ae51c-270">Добавление текста в сцену</span><span class="sxs-lookup"><span data-stu-id="ae51c-270">Adding text into your scene</span></span>

<span data-ttu-id="ae51c-271">В этом разделе вы узнаете, как добавить текст в возможности смешанной реальности с помощью Текстмеш Pro Unity, подготовленного в разделе [Импорт Текстмеш Pro Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) предыдущего руководства.</span><span class="sxs-lookup"><span data-stu-id="ae51c-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="ae51c-272">В этом конкретном примере вы добавите простую метку под коллекцией кнопок, созданной в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="ae51c-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="ae51c-273">Щелкните правой кнопкой мыши объект Буттонколлектион и выберите пункт **3D object** > **Text-текстмешпро** , чтобы создать объект текстмешпро в качестве дочернего элемента объекта буттонколлектион:</span><span class="sxs-lookup"><span data-stu-id="ae51c-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="ae51c-275">При наличии вновь созданного объекта Текстмешпро с именем text (TMP), который по-прежнему выбран, в окне инспектора измените его расположение и размер таким образом, чтобы метка располагалась под коллекцией кнопок, например:</span><span class="sxs-lookup"><span data-stu-id="ae51c-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="ae51c-276">Изменение преобразования Rect **POS Y** на-0,0425</span><span class="sxs-lookup"><span data-stu-id="ae51c-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="ae51c-277">Изменение **ширины** преобразования Rect на 0,24</span><span class="sxs-lookup"><span data-stu-id="ae51c-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="ae51c-278">Изменение **высоты** преобразования Rect на 0,024</span><span class="sxs-lookup"><span data-stu-id="ae51c-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="ae51c-279">Затем обновите текст, чтобы отразить, к чему относится метка, и выберите свойства шрифта, чтобы текст поместился в метку, например:</span><span class="sxs-lookup"><span data-stu-id="ae51c-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="ae51c-280">Изменение текстового поля Pro ( **текст** сценария) на коллекцию кнопок</span><span class="sxs-lookup"><span data-stu-id="ae51c-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="ae51c-281">Изменение **стиля шрифта** (скрипт) для текстового сетки на полужирный</span><span class="sxs-lookup"><span data-stu-id="ae51c-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="ae51c-282">Измените **Размер шрифта** Pro (скрипт) для сетки текста на 0,2</span><span class="sxs-lookup"><span data-stu-id="ae51c-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="ae51c-283">Изменение **выравнивания** (сценария) сетки текста по центру и по середине</span><span class="sxs-lookup"><span data-stu-id="ae51c-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="ae51c-285">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="ae51c-285">Congratulations</span></span>

<span data-ttu-id="ae51c-286">В этом руководстве вы узнали, как клонировать, настраивать и настраивать параметр профиля МРТК.</span><span class="sxs-lookup"><span data-stu-id="ae51c-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="ae51c-287">Вы также узнали, как взаимодействовать с кнопками для активации событий с помощью отслеживаний руки в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ae51c-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="ae51c-288">Наконец, вы узнали, как создать простой интерфейс интерфейса пользователя с помощью компонента коллекции объектов Grid МРТК и сетки текста Unity Pro.</span><span class="sxs-lookup"><span data-stu-id="ae51c-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="ae51c-289">Следующий учебник: 4. размещение динамического содержимого и использование поисковых решений</span><span class="sxs-lookup"><span data-stu-id="ae51c-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
