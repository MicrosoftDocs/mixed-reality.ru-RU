---
title: Серия руководств по началу работы, часть 3 Настройка профилей MRTK
description: Из этого курса вы узнаете, как с помощью набора средств для смешанной реальности (MRTK) создавать приложения смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2c413964a435814275a1b908770ca977412f92be
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306727"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="9af46-105">3. Настройка профилей MRTK</span><span class="sxs-lookup"><span data-stu-id="9af46-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="9af46-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="9af46-106">Overview</span></span>

<span data-ttu-id="9af46-107">Из этого руководства вы узнаете, как настраивать профили МRТК.</span><span class="sxs-lookup"><span data-stu-id="9af46-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="9af46-108">В этом конкретном примере показано, как скрыть сетку отслеживания пространственного положения, изменив параметры наблюдателя виртуальной сетки.</span><span class="sxs-lookup"><span data-stu-id="9af46-108">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="9af46-109">Те же принципы вы можете применить, чтобы настроить любые параметры или значения в профилях MRTK.</span><span class="sxs-lookup"><span data-stu-id="9af46-109">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

## <a name="objectives"></a><span data-ttu-id="9af46-110">Задачи</span><span class="sxs-lookup"><span data-stu-id="9af46-110">Objectives</span></span>

* <span data-ttu-id="9af46-111">Узнать,как настраивать профили MRTK.</span><span class="sxs-lookup"><span data-stu-id="9af46-111">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="9af46-112">Скрыть сетку отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="9af46-112">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="9af46-113">Изменить параметр отображения отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="9af46-113">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="9af46-114">Ниже приведены основные шаги, которые позволяют скрыть сетку отслеживания пространственного положения.</span><span class="sxs-lookup"><span data-stu-id="9af46-114">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="9af46-115">Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="9af46-115">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="9af46-116">Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="9af46-116">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="9af46-117">Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="9af46-117">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="9af46-118">Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="9af46-118">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="9af46-119">Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="9af46-119">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="9af46-120">По умолчанию профили MRTK недоступны для редактирования.</span><span class="sxs-lookup"><span data-stu-id="9af46-120">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="9af46-121">Это шаблоны профилей по умолчанию, которые вам нужно клонировать, прежде чем их можно будет редактировать.</span><span class="sxs-lookup"><span data-stu-id="9af46-121">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="9af46-122">Существует несколько вложенных уровней профилей.</span><span class="sxs-lookup"><span data-stu-id="9af46-122">There are several nested layers of profiles.</span></span> <span data-ttu-id="9af46-123">Таким образом, при настройке одного или нескольких параметров часто нужно клонировать и редактировать несколько профилей.</span><span class="sxs-lookup"><span data-stu-id="9af46-123">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="9af46-124">1. Клонирование профиля конфигурация по умолчанию</span><span class="sxs-lookup"><span data-stu-id="9af46-124">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="9af46-125">Профиль конфигурации является профилем верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="9af46-125">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="9af46-126">Следовательно, для изменения любых других профилей сначала необходимо клонировать профиль конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9af46-126">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="9af46-127">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор) и измените профиль конфигурации **MixedRealityToolkit** на **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="9af46-127">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="9af46-129">Сохраняя выделение объекта **MixedRealityToolkit**, в окне Inspector (Инспектор) нажмите кнопку **Copy & Customize** (Копировать и настроить), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="9af46-129">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="9af46-131">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_HoloLens2ConfigurationProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultHololens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="9af46-131">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="9af46-133">Созданный профиль конфигурации теперь назначен в качестве профиля конфигурации для сцены:</span><span class="sxs-lookup"><span data-stu-id="9af46-133">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="9af46-135">В меню Unity щелкните **File** > **Save** (Файл > Сохранить), чтобы сохранить текущую сцену.</span><span class="sxs-lookup"><span data-stu-id="9af46-135">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="9af46-136">Не забывайте сохранять работу при работе с руководством.</span><span class="sxs-lookup"><span data-stu-id="9af46-136">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="9af46-137">2. Включение системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="9af46-137">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="9af46-138">В окне Hierarchy (Иерархия) выберите объект **MixedRealityToolkit**, перейдите в окно Inspector (Инспектор), откройте вкладку **Spatial Awareness** (Отслеживание пространственного положения) и установите флажок **Enable Spatial Awareness System** (Включить систему отслеживания пространственного положения).</span><span class="sxs-lookup"><span data-stu-id="9af46-138">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="9af46-140">3. Клонирование профиля по умолчанию для системы отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="9af46-140">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="9af46-141">На вкладке **Spatial Awareness** (Отслеживание пространственного положения) нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="9af46-141">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="9af46-143">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessSystemProfile**.</span><span class="sxs-lookup"><span data-stu-id="9af46-143">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="9af46-145">Созданный профиль системы пространственного отслеживания автоматически назначается профилю конфигурации:</span><span class="sxs-lookup"><span data-stu-id="9af46-145">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="9af46-147">4. Клонирование профиля по умолчанию для наблюдателя сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="9af46-147">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="9af46-148">Оставаясь на вкладке **Spatial Awareness** (Отслеживание пространственного положения), разверните раздел **Windows Mixed Reality Spatial Mesh Observer** (Наблюдатель виртуальной сетки Windows Mixed Reality), а затем нажмите кнопку **Clone** (Клонировать), чтобы открыть окно клонирования профиля:</span><span class="sxs-lookup"><span data-stu-id="9af46-148">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="9af46-150">В окне Clone Profile (Клонирование профиля) введите понятное **имя профиля**, например _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, а затем нажмите кнопку **Clone** (Клонировать), чтобы создать доступную для редактирования копию **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**.</span><span class="sxs-lookup"><span data-stu-id="9af46-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="9af46-152">Созданный профиль для наблюдателя сетки отслеживания пространственного положения автоматически назначается профилю системы отслеживания пространственного положения:</span><span class="sxs-lookup"><span data-stu-id="9af46-152">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="9af46-154">5. Изменение видимости сетки отслеживания пространственного положения</span><span class="sxs-lookup"><span data-stu-id="9af46-154">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="9af46-155">В разделе **Spatial Mesh Observer Settings** (Параметры наблюдателя виртуальной сетки) для параметра **Display Option** (Вариант отображения) укажите значение **Occlusion** (Окклюзия), чтобы сетка пространственного картирования стала невидимой, но продолжала работать.</span><span class="sxs-lookup"><span data-stu-id="9af46-155">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="9af46-157">Хотя сетка пространственного картирования теперь не отображается, она по-прежнему присутствует и будет работать.</span><span class="sxs-lookup"><span data-stu-id="9af46-157">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="9af46-158">Например, любая голограмма позади сетки пространственного картирования не будет отображаться, как будто она находится за реальной стеной.</span><span class="sxs-lookup"><span data-stu-id="9af46-158">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="9af46-159">Вы только что узнали, как изменить параметр в профиле MRTK.</span><span class="sxs-lookup"><span data-stu-id="9af46-159">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="9af46-160">Как вы уже поняли, для настройки параметров MRTK нужно создать копии профилей по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9af46-160">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="9af46-161">Так как профили по умолчанию недоступны для редактирования, они всегда используются в качестве эталона, если вы захотите вернуться к параметрам по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9af46-161">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="9af46-162">Дополнительные сведения о профилях МRТК и их архитектуре см. в [руководстве по настройке профиля MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) на [портале документации по МRТК](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="9af46-162">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="9af46-163">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="9af46-163">Congratulations</span></span>

<span data-ttu-id="9af46-164">В этом руководстве показано, как клонировать и настраивать профили MRTK и их параметры.</span><span class="sxs-lookup"><span data-stu-id="9af46-164">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

[<span data-ttu-id="9af46-165">Следующее руководство: 4. Размещение объектов в сцене</span><span class="sxs-lookup"><span data-stu-id="9af46-165">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
