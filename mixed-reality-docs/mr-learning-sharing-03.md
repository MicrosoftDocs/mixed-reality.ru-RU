---
title: Руководства по многопользовательским возможностям, часть 3. Подключение нескольких пользователей
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5937b581e92ffc5a13b55574ffd8a0ca7c4bca40
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376396"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="ff002-105">3. Подключение нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="ff002-105">3. Connecting multiple users</span></span>

<span data-ttu-id="ff002-106">Из этого учебника вы узнаете, как подключить несколько пользователей для организации совместного взаимодействия в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="ff002-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="ff002-107">По завершении работы с этим руководством вы сможете запустить приложение на нескольких устройствах, и каждый пользователь сможет увидеть, как аватар других пользователей перемещается в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="ff002-107">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="ff002-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="ff002-108">Objectives</span></span>

* <span data-ttu-id="ff002-109">Подключение нескольких пользователей к общему взаимодействию</span><span class="sxs-lookup"><span data-stu-id="ff002-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="ff002-110">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="ff002-110">Preparing the scene</span></span>

<span data-ttu-id="ff002-111">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="ff002-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="ff002-112">В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Активы > MRTK.Tutorials.MultiUserCapabilities > Заготовки), а затем щелкните и перетащите следующие заготовки в окно Hierarchy (Иерархия), чтобы добавить их в сцену:</span><span class="sxs-lookup"><span data-stu-id="ff002-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="ff002-113">заготовка **NetworkLobby**;</span><span class="sxs-lookup"><span data-stu-id="ff002-113">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="ff002-114">заготовка **SharedPlayground**.</span><span class="sxs-lookup"><span data-stu-id="ff002-114">**SharedPlayground** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="ff002-116">В окне Project (Проект) перейдите к папке **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** (Активы > MRTK.Tutorials.AzureSpatialAnchors > Заготовки), а затем щелкните и перетащите следующие заготовки в окно Hierarchy (Иерархия), чтобы добавить их в сцену:</span><span class="sxs-lookup"><span data-stu-id="ff002-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="ff002-117">заготовка **DebugWindow**.</span><span class="sxs-lookup"><span data-stu-id="ff002-117">**DebugWindow** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="ff002-119">Создание заготовки пользователя</span><span class="sxs-lookup"><span data-stu-id="ff002-119">Creating the user prefab</span></span>

<span data-ttu-id="ff002-120">В рамках этого раздела вы создадите заготовку, которая будет использоваться для представления пользователей в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ff002-120">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="ff002-121">1. Создание и настройка пользователя</span><span class="sxs-lookup"><span data-stu-id="ff002-121">1. Create and configure the user</span></span>

<span data-ttu-id="ff002-122">Щелкните правой кнопкой мыши пустое место в окне "Иерархия" и выберите **Create Empty** (Создать пустой), чтобы добавить пустой объект в сцену. Присвойте объекту имя **PhotonUser** и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ff002-122">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="ff002-123">Убедитесь, что для свойства **Позиция** в области "Преобразование" установлены такие значения: X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="ff002-123">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="ff002-125">В окне Hierarchy (Иерархия) выберите **PhotonUser**, перейдите в окно Inspector (Инспектор) и нажмите кнопку **Add component** (Добавить компонент), чтобы добавить в объект PhotonUser компонент **Photon User (Script)** (Пользователь Photon — скрипт).</span><span class="sxs-lookup"><span data-stu-id="ff002-125">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="ff002-127">В окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Generic Net Sync (Script)** (Generic Net Sync — скрипт) и настроить его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ff002-127">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ff002-128">Установите флажок **Is User** (Пользователь).</span><span class="sxs-lookup"><span data-stu-id="ff002-128">Check the **Is User** checkbox</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="ff002-130">В окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Photon View (Script)** (Photon View — скрипт) и настроить его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ff002-130">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ff002-131">В поле **Observed Components** (Наблюдаемые компоненты) укажите компонент **Generic Net Sync (Script)** (Generic Net Sync — скрипт).</span><span class="sxs-lookup"><span data-stu-id="ff002-131">To the **Observed Components** field, assign the **Generic Net Sync (Script)** component</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="ff002-133">2. Создание аватара</span><span class="sxs-lookup"><span data-stu-id="ff002-133">2. Create the avatar</span></span>

<span data-ttu-id="ff002-134">В окне Project (Проект) перейдите к папке **Assets** > **MRTK** > **SDK** > **StandardAssets**  > **Materials** (Активы > MRTK > Пакет SDK > Стандартные активы > Материалы), чтобы найти материалы MRTK.</span><span class="sxs-lookup"><span data-stu-id="ff002-134">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="ff002-135">Затем щелкните правой кнопкой мыши объект **PhotonUser** в окне Hierarchy (Иерархия) и последовательно выберите **3D Object** > **Sphere** (Трехмерный объект > Сфера), чтобы создать сферический объект в качестве дочернего для объекта PhotonUser и настроить его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ff002-135">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ff002-136">Убедитесь, что для свойства **Позиция** в области "Преобразование" установлены такие значения: X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="ff002-136">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="ff002-137">Измените для преобразования свойство **Масштаб** до нормального размера, например X = 0,15, Y = 0,15 и Z = 0,15.</span><span class="sxs-lookup"><span data-stu-id="ff002-137">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="ff002-138">Перейдите к полю MeshRenderer > Materials (Материалы) > **Element 0** (Элемент 0) и укажите материал **MRTK_Standard_White**.</span><span class="sxs-lookup"><span data-stu-id="ff002-138">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="ff002-140">3. Создание заготовки</span><span class="sxs-lookup"><span data-stu-id="ff002-140">3. Create the prefab</span></span>

<span data-ttu-id="ff002-141">В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="ff002-141">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="ff002-143">Сохраняя выделение папки Resources (Ресурсы), **щелкните и перетащите** объект **PhotonUser** из окна "Иерархия" в папку **Resources** (Ресурсы), чтобы сделать заготовку из объекта PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="ff002-143">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="ff002-145">Щелкните правой кнопкой мыши объект **PhotonUser** в окне "Иерархия" и выберите **Удалить**, чтобы удалить его из сцены.</span><span class="sxs-lookup"><span data-stu-id="ff002-145">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="ff002-147">Настройка PUN для создания заготовки пользователя</span><span class="sxs-lookup"><span data-stu-id="ff002-147">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="ff002-148">В рамках этого раздела вы настроите проект для использования заготовки PhotonUser, созданной в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="ff002-148">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="ff002-149">В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="ff002-149">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="ff002-150">В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ff002-150">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="ff002-151">В поле **Photon User Prefab** (Заготовка пользователя Photon) укажите заготовку **PhotonUser** из папки Resources (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="ff002-151">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="ff002-153">Взаимодействие с несколькими пользователями</span><span class="sxs-lookup"><span data-stu-id="ff002-153">Trying the experience with multiple users</span></span>

<span data-ttu-id="ff002-154">Если вы теперь создадите и развернете проект Unity в HoloLens, а затем вернетесь в Unity и во время выполнения приложения на устройстве HoloLens перейдете в игровой режим, вы увидите, как с движением вашей головы (HoloLens) перемещается аватар пользователя HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ff002-154">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="ff002-156">Сведения о том, как правильно скомпилировать проект Unity и развернуть его в HoloLens 2, см. в разделе [Создание приложения для HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="ff002-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="ff002-157">Этому приложению требуется подключение к Photon, поэтому не забудьте проверить подключение компьютера или устройства к Интернету.</span><span class="sxs-lookup"><span data-stu-id="ff002-157">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ff002-158">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="ff002-158">Congratulations</span></span>

<span data-ttu-id="ff002-159">Вы успешно настроили проект. Теперь несколько пользователей могут подключаться к одному интерфейсу и просматривать перемещения друг друга.</span><span class="sxs-lookup"><span data-stu-id="ff002-159">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="ff002-160">В следующем учебнике вы реализуете функциональность, чтобы предоставить общий доступ к перемещению объектов на нескольких устройствах.</span><span class="sxs-lookup"><span data-stu-id="ff002-160">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

[<span data-ttu-id="ff002-161">Следующее руководство: 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям</span><span class="sxs-lookup"><span data-stu-id="ff002-161">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
