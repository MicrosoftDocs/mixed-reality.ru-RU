---
title: Руководства по многопользовательским возможностям, часть 3. Подключение нескольких пользователей
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031232"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="3c854-105">3. Подключение нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="3c854-105">3. Connecting multiple users</span></span>

<span data-ttu-id="3c854-106">На этом занятии мы узнаем, как подключить несколько пользователей для организации совместного взаимодействия в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="3c854-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="3c854-107">К концу этого урока вы откроете приложение на нескольких устройствах и увидите аватары в виде сфер для каждого пользователя, который присоединяется к приложению.</span><span class="sxs-lookup"><span data-stu-id="3c854-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="3c854-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="3c854-108">Objectives</span></span>

* <span data-ttu-id="3c854-109">Настройка PUN в приложении</span><span class="sxs-lookup"><span data-stu-id="3c854-109">Configure PUN within your application</span></span>
* <span data-ttu-id="3c854-110">Настройка игроков</span><span class="sxs-lookup"><span data-stu-id="3c854-110">Configure players</span></span>
* <span data-ttu-id="3c854-111">Подключение нескольких пользователей к общему взаимодействию</span><span class="sxs-lookup"><span data-stu-id="3c854-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="3c854-112">Инструкции</span><span class="sxs-lookup"><span data-stu-id="3c854-112">Instructions</span></span>

1. <span data-ttu-id="3c854-113">В папке Assets (Активы) -> Resources (Ресурсы) -> Prefabs (Заготовки) на панели проекта щелкните заготовку NetworkLobby и перетащите ее в иерархию, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="3c854-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="3c854-115">Развернув NetworkLobby, вы увидите дочерний объект с именем NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="3c854-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="3c854-116">Выбрав NetworkRoom, перейдите на панель Inspector (Инспектор) и щелкните Add Component (Добавить компонент).</span><span class="sxs-lookup"><span data-stu-id="3c854-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="3c854-117">Выполните поиск PhotonView и добавьте этот компонент.</span><span class="sxs-lookup"><span data-stu-id="3c854-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="3c854-119">Создайте в иерархии новый пустой игровой объект.</span><span class="sxs-lookup"><span data-stu-id="3c854-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="3c854-120">Щелкните иерархию правой кнопкой мыши и выберите Empty (Пустой) в контекстном меню.</span><span class="sxs-lookup"><span data-stu-id="3c854-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="3c854-121">Для положения укажите значения x = 0, y = 0, z = 0 и присвойте объекту имя PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="3c854-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="3c854-123">Нажмите кнопку Add Component (Добавить компонент) и введите "Generic Net Sync". Выберите класс Generic Net Sync.</span><span class="sxs-lookup"><span data-stu-id="3c854-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="3c854-124">Когда появится этот класс, щелкните флажок User (Пользователь), чтобы включить его.</span><span class="sxs-lookup"><span data-stu-id="3c854-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="3c854-126">Снова нажмите кнопку Add Component (Добавить компонент) и введите "Photon View".</span><span class="sxs-lookup"><span data-stu-id="3c854-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="3c854-127">Выберите класс Photon View, который появится в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="3c854-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="3c854-129">Щелкните значок файла для класса Generic Net Sync.</span><span class="sxs-lookup"><span data-stu-id="3c854-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="3c854-130">Перетащите его в поле Observed Components (Наблюдаемые компоненты) в представлении Photon.</span><span class="sxs-lookup"><span data-stu-id="3c854-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="3c854-132">Теперь мы создадим сферы, которые будут представлять каждого человека, который присоединяется к общему взаимодействию.</span><span class="sxs-lookup"><span data-stu-id="3c854-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="3c854-133">Щелкните правой кнопкой мыши объект PhotonUser, который вы только что создали, прокрутите содержимое вниз до пункта 3D Object (Трехмерный объект) и щелкните Sphere (Сфера).</span><span class="sxs-lookup"><span data-stu-id="3c854-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="3c854-134">Этот процесс создает игровой объект Sphere (Сфера) в качестве дочернего объекта для PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="3c854-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="3c854-136">Назначьте этой сфере размеры x = 0,06, y = 0,06 и z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="3c854-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="3c854-138">Перетащите игровой объект PhotonUser в папку Prefabs (Заготовки) на панели проекта, а затем удалите его из сцены.</span><span class="sxs-lookup"><span data-stu-id="3c854-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="3c854-139">Так вы создали заготовку, которую можно использовать при создании экземпляров для новых игроков в общем взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="3c854-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="3c854-141">Убедитесь, что игровой объект успешно скопирован в папку Prefabs (Заготовки), прежде чем удалять его из иерархии.</span><span class="sxs-lookup"><span data-stu-id="3c854-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="3c854-142">Создайте еще один объект в иерархии, повторив процедуру из шага 3, и присвойте ему имя SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="3c854-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="3c854-143">Теперь щелкните Add Component (Добавить компонент) и найдите "generic network manager".</span><span class="sxs-lookup"><span data-stu-id="3c854-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="3c854-144">Щелкните компонент Generic Network Manager (Универсальный диспетчер сети), чтобы добавить его.</span><span class="sxs-lookup"><span data-stu-id="3c854-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="3c854-145">Укажите для этого объекта положение x = 0, y = 0 и z = 0.</span><span class="sxs-lookup"><span data-stu-id="3c854-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="3c854-147">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="3c854-147">Congratulations</span></span>

<span data-ttu-id="3c854-148">Завершив все описанные выше шаги и дождавшись окончания процесса сборки, нажмите кнопку Play (Играть) и подключите устройство HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3c854-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="3c854-149">Вы увидите, как сфера в сцене перемещается синхронно с движениями вашей головы.</span><span class="sxs-lookup"><span data-stu-id="3c854-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="3c854-150">Это будет видно любому пользователю, который подключится к этому проекту Unity.</span><span class="sxs-lookup"><span data-stu-id="3c854-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="3c854-151">[Следующий урок. 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="3c854-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>
