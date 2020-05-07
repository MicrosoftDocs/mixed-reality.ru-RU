---
title: Руководства по многопользовательским возможностям, часть 3. Подключение нескольких пользователей
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610893"
---
# <a name="2-connecting-multiple-users"></a><span data-ttu-id="ad1c3-105">2. Подключение нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="ad1c3-105">2. Connecting multiple users</span></span>

<span data-ttu-id="ad1c3-106">Из этого учебника вы узнаете, как подключить несколько пользователей для организации совместного взаимодействия в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="ad1c3-107">По завершении работы с этим учебником вы сможете запустить приложение на нескольких устройствах, и каждый пользователь сможет увидеть, как аватар других пользователей перемещается в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-107">By the end of the tutorial you will be able to run the application on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="ad1c3-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="ad1c3-108">Objectives</span></span>

* <span data-ttu-id="ad1c3-109">Подключение нескольких пользователей к общему взаимодействию</span><span class="sxs-lookup"><span data-stu-id="ad1c3-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="ad1c3-110">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="ad1c3-110">Preparing the scene</span></span>

<span data-ttu-id="ad1c3-111">В рамках этого раздела вы подготовите сцену, добавив в нее несколько заготовок для руководства.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="ad1c3-112">В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки).</span><span class="sxs-lookup"><span data-stu-id="ad1c3-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder.</span></span> <span data-ttu-id="ad1c3-113">Удерживая нажатой клавишу CTRL, щелкните заготовки **DebugWindow**, **NetworkLobby** и **SharedPlayground**, чтобы выбрать их.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-113">While holding down the CTRL button, click on **DebugWindow**, **NetworkLobby**, and **SharedPlayground** to select the three prefabs:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

<span data-ttu-id="ad1c3-115">Когда все три заготовки будут выбраны, перетащите их вместе в окно "Иерархия", чтобы добавить в сцену:</span><span class="sxs-lookup"><span data-stu-id="ad1c3-115">With the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="ad1c3-117">Создание заготовки пользователя</span><span class="sxs-lookup"><span data-stu-id="ad1c3-117">Creating the user prefab</span></span>

<span data-ttu-id="ad1c3-118">В рамках этого раздела вы создадите заготовку, которая будет использоваться для представления пользователей в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-118">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="ad1c3-119">1. Создание и настройка пользователя</span><span class="sxs-lookup"><span data-stu-id="ad1c3-119">1. Create and configure the user</span></span>

<span data-ttu-id="ad1c3-120">Щелкните правой кнопкой мыши пустое место в окне "Иерархия" и выберите **Create Empty** (Создать пустой), чтобы добавить пустой объект в сцену. Присвойте объекту имя **PhotonUser** и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-120">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="ad1c3-121">Убедитесь, что для свойства **Позиция** в области "Преобразование" установлены такие значения: X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-121">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

<span data-ttu-id="ad1c3-123">Сохраняя выделение объекта **PhotonUser**, в окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Photon User (Script)** (Пользователь Photon — скрипт).</span><span class="sxs-lookup"><span data-stu-id="ad1c3-123">With the **PhotonUser** object still selected, in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

<span data-ttu-id="ad1c3-125">В окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Generic Net Sync (Script)** (Generic Net Sync — скрипт) и настроить его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-125">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ad1c3-126">Установите флажок **Is User** (Пользователь).</span><span class="sxs-lookup"><span data-stu-id="ad1c3-126">Check the **Is User** checkbox</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

<span data-ttu-id="ad1c3-128">В окне "Инспектор" нажмите кнопку **Добавить компонент**, чтобы добавить в объект PhotonUser компонент **Photon View (Script)** (Photon View — скрипт) и настроить его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-128">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ad1c3-129">В поле **Observed Components** (Наблюдаемые компоненты) укажите компонент Generic Net Sync (Script) (Generic Net Sync — скрипт).</span><span class="sxs-lookup"><span data-stu-id="ad1c3-129">To the **Observed Components** field, assign the Generic Net Sync (Script) component</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="ad1c3-131">2. Создание аватара</span><span class="sxs-lookup"><span data-stu-id="ad1c3-131">2. Create the avatar</span></span>

<span data-ttu-id="ad1c3-132">Щелкните правой кнопкой мыши объект **PhotonUser** в окне "Иерархия" и последовательно выберите **3D Object** > **Sphere** (Трехмерный объект > Сфера), чтобы создать сферический объект в качестве дочернего для объекта PhotonUser и настроить его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-132">In the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="ad1c3-133">Убедитесь, что для свойства **Позиция** в области "Преобразование" установлены такие значения: X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-133">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="ad1c3-134">Измените для преобразования свойство **Масштаб** до нормального размера, например X = 0,15, Y = 0,15 и Z = 0,15.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-134">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="ad1c3-136">3. Создание заготовки</span><span class="sxs-lookup"><span data-stu-id="ad1c3-136">3. Create the prefab</span></span>

<span data-ttu-id="ad1c3-137">В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="ad1c3-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

<span data-ttu-id="ad1c3-139">Сохраняя выделение папки Resources (Ресурсы), **щелкните и перетащите** объект **PhotonUser** из окна "Иерархия" в папку **Resources** (Ресурсы), чтобы сделать заготовку из объекта PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-139">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

<span data-ttu-id="ad1c3-141">Щелкните правой кнопкой мыши объект **PhotonUser** в окне "Иерархия" и выберите **Удалить**, чтобы удалить его из сцены.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-141">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="ad1c3-143">Настройка PUN для создания заготовки пользователя</span><span class="sxs-lookup"><span data-stu-id="ad1c3-143">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="ad1c3-144">В рамках этого раздела вы настроите проект для использования заготовки PhotonUser, созданной в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-144">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="ad1c3-145">В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="ad1c3-145">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="ad1c3-146">В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-146">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="ad1c3-147">В поле **Photon User Prefab** (Заготовка пользователя Photon) укажите заготовку **PhotonUser** из папки Resources (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="ad1c3-147">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="ad1c3-149">Взаимодействие с несколькими пользователями</span><span class="sxs-lookup"><span data-stu-id="ad1c3-149">Trying the experience with multiple users</span></span>

<span data-ttu-id="ad1c3-150">Если вы теперь создадите и развернете проект Unity в HoloLens, а затем, вернувшись в Unity, во время выполнения приложения на устройстве HoloLens нажмете кнопку Play (Играть), чтобы перейти в игровой режим, вы увидите, как с движением вашей головы (HoloLens) перемещается аватар пользователя HoloLens:</span><span class="sxs-lookup"><span data-stu-id="ad1c3-150">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="ad1c3-152">Чтобы вспомнить, как правильно скомпилировать проект Unity и развернуть его на HoloLens 2, воспользуйтесь инструкциями из раздела о [разработке приложения для устройства](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="ad1c3-152">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="ad1c3-153">Этому приложению требуется подключение к Photon, поэтому не забудьте проверить связь компьютера или устройства с Интернетом.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-153">The application needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ad1c3-154">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="ad1c3-154">Congratulations</span></span>

<span data-ttu-id="ad1c3-155">Вы успешно настроили проект. Теперь несколько пользователей могут подключаться к одному интерфейсу и просматривать перемещения друг друга.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-155">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="ad1c3-156">В следующем учебнике вы реализуете функциональность, чтобы предоставить общий доступ к перемещению объектов на нескольких устройствах.</span><span class="sxs-lookup"><span data-stu-id="ad1c3-156">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

<span data-ttu-id="ad1c3-157">[Следующее руководство: 2. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="ad1c3-157">[Next tutorial: 2. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
