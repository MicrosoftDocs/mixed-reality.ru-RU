---
title: Серия руководств по началу работы, часть 3 Создание пользовательского интерфейса и настройка Набора средств для смешанной реальности
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376141"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="5c6e3-105">3. Создание пользовательского интерфейса и настройка Набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="5c6e3-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="5c6e3-106">В предыдущем руководстве вы изучили некоторые возможности Набора средств для смешанной реальности (MRTK) на примере простейшего приложения для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="5c6e3-107">Из этого руководства вы узнаете, как создать и упорядочить кнопки и текстовые панели пользовательского интерфейса, а также как применить для каждой из кнопок взаимодействие по умолчанию (касание).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="5c6e3-108">Кроме того, вы освоите добавление простых действий и эффектов, например изменение размера, звука и цвета для объектов.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="5c6e3-109">В этом модуле представлены основные понятия, связанные с изменением профилей MRTK, начиная с отключения визуализации сетки для [пространственного картирования](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="5c6e3-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="5c6e3-110">Objectives</span></span>

* <span data-ttu-id="5c6e3-111">Настройка профилей набора средств для смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="5c6e3-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="5c6e3-112">Взаимодействие с голограммами через кнопки и элементы пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="5c6e3-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="5c6e3-113">Базовый ввод данных и взаимодействие с помощью средства отслеживания руки</span><span class="sxs-lookup"><span data-stu-id="5c6e3-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="5c6e3-114">Настройка профилей Набора средств для смешанной реальности (изменение параметра отображения для отслеживания пространственного положения)</span><span class="sxs-lookup"><span data-stu-id="5c6e3-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="5c6e3-115">Из этого раздела вы узнаете, как настраивать профили МRТК по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="5c6e3-116">В этом конкретном примере показано, как скрыть сетку отслеживания пространственного положения, изменив параметры наблюдателя виртуальной сетки.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="5c6e3-117">Те же принципы вы можете применить, чтобы настроить любые параметры или значения в профилях MRTK.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="5c6e3-118">Ниже приведены основные шаги, которые позволяют скрыть сетку отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="5c6e3-119">Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="5c6e3-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="5c6e3-120">Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="5c6e3-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="5c6e3-121">Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="5c6e3-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="5c6e3-122">Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="5c6e3-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="5c6e3-123">Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="5c6e3-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="5c6e3-124">По умолчанию профили MRTK недоступны для редактирования.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="5c6e3-125">Это шаблоны профилей по умолчанию, которые вам нужно клонировать, прежде чем их можно будет редактировать.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="5c6e3-126">Существует несколько вложенных уровней профилей.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="5c6e3-127">Таким образом, при настройке одного или нескольких параметров часто нужно клонировать и редактировать несколько профилей.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="5c6e3-128">1. Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="5c6e3-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="5c6e3-129">Профиль конфигурации расположен на высшем уровне профилей.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="5c6e3-130">Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="5c6e3-131">Выбрав объект **MixedRealityToolkit** в окне Hierarchy (Иерархия), перейдите в окно Inspector (Инспектор) и измените **профиль конфигурации** Набора средств для смешанной реальности на **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="5c6e3-133">Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="5c6e3-135">В окне клонирования профиля нажмите кнопку **Клонировать**, чтобы создать изменяемую копию **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="5c6e3-137">Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="5c6e3-139">В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="5c6e3-140">Не забывайте сохранять работу при работе с руководством.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="5c6e3-141">2. Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="5c6e3-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="5c6e3-142">Сохраняя выделение объекта **MixedRealityToolkit** в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) выберите вкладку **Spatial Awareness** (Отслеживание пространственного положения), а затем установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="5c6e3-144">3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="5c6e3-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="5c6e3-145">На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="5c6e3-147">В окне клонирования профиля нажмите кнопку **Clone** (Клонировать), чтобы создать редактируемую копию **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="5c6e3-149">Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="5c6e3-151">4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="5c6e3-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="5c6e3-152">Оставаясь на вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель виртуальной сетки Windows Mixed Reality), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="5c6e3-154">В окне клонирования профиля нажмите кнопку **Clone** (Клонировать), чтобы создать изменяемую копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="5c6e3-156">Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="5c6e3-158">5. Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="5c6e3-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="5c6e3-159">В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Перекрытия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="5c6e3-161">Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="5c6e3-162">Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="5c6e3-163">Вы только что узнали, как изменить параметр в профиле MRTK.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="5c6e3-164">Как вы уже поняли, для настройки параметров MRTK нужно создать копии стандартных профилей.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="5c6e3-165">Так как стандартные профили недоступны для редактирования, они всегда используются в качестве справочного варианта, если придется вернуться к параметрам по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="5c6e3-166">Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля для Набора средств для смешанной реальности](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) на [портале документации по МRТК](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="5c6e3-167">Обработка жестов и нажатий активных кнопок с помощью технологии отслеживания рук</span><span class="sxs-lookup"><span data-stu-id="5c6e3-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="5c6e3-168">Из этого раздела вы узнаете, как использовать отслеживание рук для нажатия кнопок и запуска событий, чтобы вызвать действие при нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="5c6e3-169">В этом конкретном примере показано, как изменить цвет куба при нажатии кнопки и вернуть исходный цвет при отпускании кнопки.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="5c6e3-170">Но такими же методами вы можете создавать любые другие события.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="5c6e3-171">Основные действия, которые нужно выполнить для изменения цвета куба:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="5c6e3-172">Добавление заготовки нажимаемой кнопки в сцену.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="5c6e3-173">Добавление куба в сцену.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="5c6e3-174">Настройка типа события InteractableOnPressReceiver.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="5c6e3-175">Настройка куба для получения события OnPress.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="5c6e3-176">Определение действия, запускаемого событием OnPress.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="5c6e3-177">Настройка куба для получения события OnRelease.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="5c6e3-178">Определение действия, запускаемого событием OnRelease.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="5c6e3-179">Тестирование кнопки с помощью имитации в редакторе.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="5c6e3-180">1. Добавление заготовки нажимаемой кнопки в сцену</span><span class="sxs-lookup"><span data-stu-id="5c6e3-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="5c6e3-181"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Заготовкой</a> называется предварительно настроенный игровой объект (GameObject), который хранится в качестве актива Unity и может повторно использоваться в проекте.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="5c6e3-182">В **окне проекта** в строку поиска введите запрос **PressableButtonHoloLens2**, чтобы найти заготовку для этого примера:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="5c6e3-184">В **результатах поиска** выберите заготовку **PressableButtonHoloLens2** и **перетащите** ее в окно **Hierarchy** (Иерархия), чтобы добавить в сцену:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="5c6e3-186">Для отображения сцены, как на рисунке ниже, дважды щелкните объект PressableButtonHoloLens2 в окне Hierarchy (Иерархия), чтобы перевести на него фокус, а затем используйте <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Манипулятор сцены) в правом верхнем углу окна сцены, чтобы направить угол взгляда вдоль оси Z вперед.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="5c6e3-187">Сохраняя выделение объекта **PressableButtonHoloLens2**, в окне **Inspector** (Инспектор) выполните следующее:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="5c6e3-188">Измените для преобразования свойство **Position** (Положение) так, чтобы объект оказался перед камерой, размещенной в точке начала координат, например в точке с координатами x = 0, y = 0 и z = 0,5.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="5c6e3-190">Обычно одна единица положения в Unity примерно эквивалентна одному метру в реальных условиях.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="5c6e3-191">Но из этого правила могут быть исключения, например для дочерних объектов масштабированных объектов.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="5c6e3-192">2. Добавление куба в сцену</span><span class="sxs-lookup"><span data-stu-id="5c6e3-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="5c6e3-193">Щелкните правой кнопкой мыши пустое место в окне Hierarchy (Иерархия) и выберите **3D Object** > **Cube** (Трехмерный объект > Куб), чтобы добавить куб в сцену:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="5c6e3-195">Сохраняя выделение объекта **Cube** (Куб), в окне **Inspector** (Инспектор) выполните следующее:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="5c6e3-196">Измените для преобразования свойство **Position** (Положение) так, чтобы объект оказался рядом с нажимаемой кнопкой, но не перекрыл ее, например в точке с координатами x = 0, y = 0,04 и z = 0,5.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="5c6e3-197">Измените для преобразования свойство **Scale** (Масштаб) до нормального размера, например x = 0,02, y = 0,02 и z = 0,02.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="5c6e3-199">3. Настройка типа события InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="5c6e3-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="5c6e3-200">В окне Hierarchy (Иерархия) выберите объект **PressableButtonHoloLens2**, затем в окне **Inspector** (Инспектор) откройте **меню "гамбургер"** и выберите **Collapse All Components** (Свернуть все компоненты), чтобы получить представление о компонентах этого объекта:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="5c6e3-202">Разверните компонент **Interactable (Script)** (Интерактивный — скрипт), затем найдите и разверните раздел **Events** > **Receivers** (События > Получатели):</span><span class="sxs-lookup"><span data-stu-id="5c6e3-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="5c6e3-204">Щелкните кнопку **Add Event** (Добавить событие), чтобы создать получатель события с типом **InteractableOnPressReceiver**:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="5c6e3-206">Тип получателя событий InteractableOnPressReceiver отвечает за реагирование кнопки на событие нажатия, когда отслеживаемая рука нажимает эту кнопку.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="5c6e3-207">Для нового получателя событий измените значение параметра **Interaction Filter** (Фильтр взаимодействия) на **Near and Far** (Ближнее и дальнее):</span><span class="sxs-lookup"><span data-stu-id="5c6e3-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="5c6e3-209">4. Настройка куба для получения события OnPress</span><span class="sxs-lookup"><span data-stu-id="5c6e3-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="5c6e3-210">В окне Hierarchy (Иерархия) **щелкните и перетащите** объект **Cube** в поле объекта **Event Properties** (Свойства события), отвечающее за событие **On Press ()** , чтобы назначить этот куб получателем события OnPress() этого объекта:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="5c6e3-212">5. Определение действия, запускаемого событием OnPress</span><span class="sxs-lookup"><span data-stu-id="5c6e3-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="5c6e3-213">Щелкните раскрывающийся список действий, где сейчас выбран вариант **No Function** (Без действий), и выберите **MeshRenderer** > **Material material** (Материал material), чтобы значение материала куба изменялось при срабатывании события OnPress:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="5c6e3-215">Щелкните небольшой значок в форме **круга** рядом с полем материала, где сейчас выбран вариант **None (Material)** (Нет (материал)), чтобы открыть окно выбора материала:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="5c6e3-217">В окне выбора материала выполните **поиск** по строке **MRTK_Standard** и выберите подходящий материал, например **MRTK_Standard_Cyan**, чтобы изменять цвет куба при нажатии кнопки:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="5c6e3-219">6. Настройка куба для получения события OnRelease</span><span class="sxs-lookup"><span data-stu-id="5c6e3-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="5c6e3-220">**Повторите** шаг 4 для события OnRelease, назначив тот же объект **Cube** в качестве получателя события **On Release ()** .</span><span class="sxs-lookup"><span data-stu-id="5c6e3-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="5c6e3-221">7. Определение действия, запускаемого событием OnRelease</span><span class="sxs-lookup"><span data-stu-id="5c6e3-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="5c6e3-222">**Повторите** шаг 5 для события OnRelease, но теперь выберите материал **MRTK_Standard_LightGray**, чтобы куб возвращался к исходному светло-серому цвету при отпускании кнопки:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="5c6e3-224">8. Тестирование кнопки с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="5c6e3-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="5c6e3-225">Нажмите кнопку **Play** (Играть), чтобы перейти в игровой режим встроенного имитатора ввода и протестировать только что настроенные действия кнопки.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="5c6e3-226">Кнопка не нажата (пробел и вращение колесика мыши назад):</span><span class="sxs-lookup"><span data-stu-id="5c6e3-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="5c6e3-228">Кнопка нажата (пробел и вращение колесика мыши вперед):</span><span class="sxs-lookup"><span data-stu-id="5c6e3-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="5c6e3-230">Сведения о том, как можно использовать встроенный имитатор ввода, см. в руководстве [по использованию имитации ввода с помощью рук в редакторе для тестирования сцены](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene), размещенному на [портале документации MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="5c6e3-231">Создание панели кнопок с помощью коллекции объектов сетки MRTK</span><span class="sxs-lookup"><span data-stu-id="5c6e3-231">Creating a panel of buttons using MRTK's Grid Object Collection</span></span>

<span data-ttu-id="5c6e3-232">Из этого раздела вы узнаете, как реализовать автоматическое выравнивание нескольких кнопок с помощью средства GridObjectCollection из MRTK, чтобы получить аккуратный пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK's Grid Object Collection tool.</span></span>

<span data-ttu-id="5c6e3-233">В этом примере показано, как создать панель с пятью кнопками, выровненными по горизонтали.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="5c6e3-234">Но такими же методами вы можете создавать любые другие макеты.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="5c6e3-235">Для получения этого результата вам нужно выполнить следующие шаги:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="5c6e3-236">Присвоение родительского объекта для объектов кнопок</span><span class="sxs-lookup"><span data-stu-id="5c6e3-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="5c6e3-237">Добавление и настройка компонента Grid Object Collection (Script) (Коллекция объектов сетки — скрипт).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="5c6e3-238">Тестирование кнопок с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="5c6e3-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="5c6e3-239">1. Присвоение родительского объекта для объектов кнопок</span><span class="sxs-lookup"><span data-stu-id="5c6e3-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="5c6e3-240">Щелкните правой кнопкой мыши пустое место в окне Hierarchy (Иерархия) и выберите **Create Empty** (Создать пустой):</span><span class="sxs-lookup"><span data-stu-id="5c6e3-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="5c6e3-242">Щелкните новый объект правой кнопкой мыши, выберите **Rename** (Переименовать) и присвойте ему подходящее имя, например **ButtonCollection**:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="5c6e3-244">Выберите объект **PressableButtonHoloLens2** и **перетащите** его поверх объекта **ButtonCollection**, чтобы сделать его дочерним для объекта ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="5c6e3-246">Щелкните объект **PressableButtonHoloLens2** правой кнопкой мыши и выберите действие **Duplicate** (Дублировать), чтобы создать копию этого объекта:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="5c6e3-248">**Повторите** этот шаг еще четыре раза, чтобы получить пять объектов PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="5c6e3-249">2. Добавление и настройка компонента Grid Object Collection (Script) (Коллекция объектов сетки — скрипт).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="5c6e3-250">Сохраняя выбранным объект ButtonCollection в окне Hierarchy (Иерархия), щелкните в окне Inspector (Инспектор) кнопку **Add Component** (Добавить компонент), затем найдите и выберите **Grid Object Collection** (Коллекция объектов сетки), чтобы добавить компонент "Grid Object Collection (Script)" (Коллекция объектов сетки — скрипт) к объекту ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="5c6e3-252">Настройте компонент "Grid Object Collection (Script)" (Коллекция объектов сетки — скрипт) следующим образом.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="5c6e3-253">Для параметра **Num Rows** (Число строк) установите значение 1, чтобы все кнопки разместились в одном ряду.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="5c6e3-254">Для параметра **Cell Width** (Ширина ячейки) установите значение 0,05, чтобы задать расстояние между кнопками в одном ряду.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="5c6e3-255">Нажмите кнопку **Update Collection** (Обновить коллекцию), чтобы применить новую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="5c6e3-257">Изменения конфигурации, которые вы только что применили, — это минимально необходимый набор настроек для размещения кнопок в один горизонтальный ряд.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="5c6e3-258">Но в будущих проектах, в зависимости от ориентации родительского и дочерних объектов и (или) других факторов, может потребоваться изменить и другие параметры, например Orient Type (Тип ориентации).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="5c6e3-259">Дополнительные сведения о компоненте Grid Object Collection (Коллекция объектов сетки) в MRTK вы можете найти в [руководстве по коллекции скриптов](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) на [портале документации по MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="5c6e3-260">Сохраняя выбранным объект ButtonCollection в окне Hierarchy (Иерархия), в окне Inspector (Инспектор) измените для этого объекта ButtonCollection значение преобразования **Position** (Положение), чтобы его дочерние объекты располагались перед камерой, размещенной в точке начала координат, например в точке с координатами x = 0, y = 0, и z = 0,5.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="5c6e3-262">При первом добавлении в сцену заготовки PressableButtonHoloLens2, как описано выше в разделе [Обработка жестов и нажатий активных кнопок с помощью технологии отслеживания рук](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons), вы разместили эту заготовку перед камерой.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="5c6e3-263">Но из-за того, что коллекция объектов сетки определяет положение своих дочерних объектов, для дочернего объекта PressableButtonHoloLens2 положение по оси Z было автоматически сброшено на 0 в соответствии со значением 0 у параметра "Distance from parent" (Дистанция от родительского объекта) в объекте Grid Object Collection (Коллекция объектов сетки).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="5c6e3-264">По этой причине, а также для упорядоченности положений родительских и дочерних объектов, мы переместили объект ButtonCollection вперед, вместо того, чтобы изменять значение параметра "Distance from parent" (Дистанция от родительского объекта) для смещения дочернего объекта PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="5c6e3-265">3. Тестирование кнопок с помощью имитации в редакторе</span><span class="sxs-lookup"><span data-stu-id="5c6e3-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="5c6e3-266">Нажмите кнопку Play (Играть), чтобы перейти в игровой режим и с помощью встроенного имитатора ввода протестировать кнопки в только что созданном наборе кнопок.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="5c6e3-268">Теперь, если нажать любую из пяти кнопок, куб станет голубым.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="5c6e3-269">Чтобы взаимодействие стало интереснее, настройте для каждой кнопки другой цвет куба, используя полученные в этом руководстве знания.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="5c6e3-270">Добавление текста в сцену</span><span class="sxs-lookup"><span data-stu-id="5c6e3-270">Adding text into your scene</span></span>

<span data-ttu-id="5c6e3-271">Из этого раздела вы узнаете, как добавить текст в интерфейс для смешанной реальности с помощью объекта TextMesh Pro, который вы подготовили в разделе [Импорт требуемых ресурсов TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) предыдущего руководства.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="5c6e3-272">В этом конкретном примере вы добавите простую метку под коллекцией кнопок, которую вы создали в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="5c6e3-273">Щелкните правой кнопкой объект ButtonCollection и выберите элементы **3D Object** > **Text — TextMeshPro** (Трехмерный объект > Текст — TextMeshPro), чтобы создать объект TextMeshPro в качестве дочернего для объекта ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="5c6e3-275">Сохраняя выделение только что созданного объекта TextMesh Pro, измените его положение и размер в окне Inspector (Инспектор) так, чтобы объект был расположен прямо под коллекцией кнопок, например так:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="5c6e3-276">в разделе Rect Transform укажите для **Pos Y** значение -0,0425;</span><span class="sxs-lookup"><span data-stu-id="5c6e3-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="5c6e3-277">в разделе Rect Transform укажите для **Width** значение 0,24;</span><span class="sxs-lookup"><span data-stu-id="5c6e3-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="5c6e3-278">в разделе Rect Transform укажите для **Height** значение 0,024.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="5c6e3-279">Теперь измените текст с учетом назначения этой метки и выберите параметры шрифта для аккуратного размещения этого текста на метке, например так:</span><span class="sxs-lookup"><span data-stu-id="5c6e3-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="5c6e3-280">в разделе Text Mesh Pro (Script) укажите для **Text** (Текст) значение Button Collection (Коллекция кнопок);</span><span class="sxs-lookup"><span data-stu-id="5c6e3-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="5c6e3-281">в разделе Text Mesh Pro (Script) укажите для **Font Style** (Стиль шрифта) значение Bold (Полужирный);</span><span class="sxs-lookup"><span data-stu-id="5c6e3-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="5c6e3-282">в разделе Text Mesh Pro (Script) укажите для **Font Size** (Размер шрифта) значение 0,2;</span><span class="sxs-lookup"><span data-stu-id="5c6e3-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="5c6e3-283">в разделе Text Mesh Pro (Script) укажите для **Alignment** (Выравнивание) значения Center (по центру) и Middle (посередине).</span><span class="sxs-lookup"><span data-stu-id="5c6e3-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="5c6e3-285">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="5c6e3-285">Congratulations</span></span>

<span data-ttu-id="5c6e3-286">В рамках этого руководства вы научились клонировать и настраивать параметр профиля MRTK.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="5c6e3-287">Кроме того, вы узнали, как вызывать события для кнопок с помощью функции отслеживания рук в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="5c6e3-288">Наконец, вы создали простой пользовательский интерфейс с помощью компонента коллекции объектов сетки в MRTK и объекта Text Mesh Pro в Unity.</span><span class="sxs-lookup"><span data-stu-id="5c6e3-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="5c6e3-289">Следующее руководство: 4. Размещение динамического содержимого и использование решателей</span><span class="sxs-lookup"><span data-stu-id="5c6e3-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
