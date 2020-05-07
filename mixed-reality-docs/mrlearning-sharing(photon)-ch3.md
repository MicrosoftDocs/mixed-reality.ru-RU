---
title: Руководства по многопользовательским возможностям, часть 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610627"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="088e1-105">3. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям</span><span class="sxs-lookup"><span data-stu-id="088e1-105">3. Sharing object movements with multiple users</span></span>

<span data-ttu-id="088e1-106">В этом учебнике вы узнаете, как совместно использовать перемещения объектов, чтобы все участники общего интерфейса могли взаимодействовать друг с другом и наблюдать эти взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="088e1-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each others' interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="088e1-107">Задачи</span><span class="sxs-lookup"><span data-stu-id="088e1-107">Objectives</span></span>

* <span data-ttu-id="088e1-108">Настройка проекта для совместного использования перемещений объектов</span><span class="sxs-lookup"><span data-stu-id="088e1-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="088e1-109">Создание простого многопользовательского приложения для совместной работы</span><span class="sxs-lookup"><span data-stu-id="088e1-109">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="088e1-110">Подготовка сцены</span><span class="sxs-lookup"><span data-stu-id="088e1-110">Preparing the scene</span></span>

<span data-ttu-id="088e1-111">В рамках этого раздела вы подготовите сцену, добавив в нее заготовку для учебника.</span><span class="sxs-lookup"><span data-stu-id="088e1-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="088e1-112">В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Заготовки) и перетащите заготовку **TableAnchor** поверх объекта **SharedPlayground** в окне "Иерархия", чтобы добавить ее в сцену в качестве дочернего элемента объекта SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="088e1-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab on top of the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="088e1-114">Настройка PUN для создания объектов</span><span class="sxs-lookup"><span data-stu-id="088e1-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="088e1-115">В рамках этого раздела вы настроите проект для использования заготовки RocketLauncher_Complete_Variant, которую вы создали в предыдущем разделе, а также определите, где она будет создана.</span><span class="sxs-lookup"><span data-stu-id="088e1-115">In this section, you will configure the project to use the RocketLauncher_Complete_Variant prefab you created in the previous section and define where it will be instantiated.</span></span>

<span data-ttu-id="088e1-116">В окне "Проект" перейдите к папке **Assets** (Активы) > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="088e1-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="088e1-117">В окне "Иерархия" разверните объект **NetworkLobby** и выберите дочерний объект **NetworkRoom**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="088e1-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="088e1-118">В поле **Photon User Prefab** (Заготовка пользователя Photon) укажите заготовку **PhotonUser** из папки Resources (Ресурсы).</span><span class="sxs-lookup"><span data-stu-id="088e1-118">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

<span data-ttu-id="088e1-120">Сохраняя выделение объекта **NetworkRoom**, в окне "Иерархия" разверните объект **TableAnchor**. Затем в окне "Инспектор" найдите компонент **Photon Room (Script)** (Photon Room — скрипт) и настройте его, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="088e1-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="088e1-121">В поле **Rocket Launcher Location** (Расположение Rocket Launcher) укажите дочерний объект **Table** из окна "Иерархия".</span><span class="sxs-lookup"><span data-stu-id="088e1-121">To the **Rocket Launcher Location** field, assign the **Table** child object from the Hierarchy window</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="088e1-123">Использование возможности общего перемещения объектов</span><span class="sxs-lookup"><span data-stu-id="088e1-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="088e1-124">Если вы теперь создадите и развернете проект Unity в HoloLens, а затем, вернувшись в Unity, во время выполнения приложения на устройстве HoloLens нажмете кнопку Play (Играть), чтобы перейти в игровой режим, вы увидите, как при перемещении объекта в HoloLens перемещается объект в Unity:</span><span class="sxs-lookup"><span data-stu-id="088e1-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="088e1-126">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="088e1-126">Congratulations</span></span>

<span data-ttu-id="088e1-127">Вы успешно настроили проект. Теперь перемещения объектов синхронизированы и пользователи могут видеть, как перемещаются объекты, когда их перемещают другие пользователи.</span><span class="sxs-lookup"><span data-stu-id="088e1-127">You have successfully configured your project so object movements are synchronized and users can see the objects move when other users move the objects.</span></span> <span data-ttu-id="088e1-128">В следующем учебнике вы реализуете функциональность для согласования общего интерфейса в реальном мире, чтобы пользователи увидели друг друга в их фактическом физическом расположении, а объекты отображались в одинаковом физическом положении и повороте для всех пользователей.</span><span class="sxs-lookup"><span data-stu-id="088e1-128">In the next tutorial, you will implement functionality so the shared experience is aligned in the physical world and the users see each other in their actual physical location and so the objects appear in the same physical position and rotation for all users.</span></span>

<span data-ttu-id="088e1-129">[Следующее руководство: 4. Интеграция Пространственных привязок Azure в общий интерфейс](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="088e1-129">[Next tutorial: 4. Integrating Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch4.md)</span></span>
