---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 33f265c6333f12f7ec73ecb0c1e5730b168d4bde
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415915"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="7bdf9-104">**Подключение нескольких пользователей**</span><span class="sxs-lookup"><span data-stu-id="7bdf9-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="7bdf9-105">На этом занятии будет рассказано подключение нескольких пользователей как часть общих условий работы пользователей.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="7bdf9-106">К концу урока можно открыть приложение на нескольких устройствах и см. в разделе «аватар» представления каждого, кто присоединяется (представленный сферы аватары.)</span><span class="sxs-lookup"><span data-stu-id="7bdf9-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="7bdf9-107">Цели:</span><span class="sxs-lookup"><span data-stu-id="7bdf9-107">Objectives:</span></span>

- <span data-ttu-id="7bdf9-108">Настройка СОВМЕСТНОЙ в вашем приложении</span><span class="sxs-lookup"><span data-stu-id="7bdf9-108">Configure PUN within your application</span></span>
- <span data-ttu-id="7bdf9-109">Настройки игрокам</span><span class="sxs-lookup"><span data-stu-id="7bdf9-109">Configure players</span></span>
- <span data-ttu-id="7bdf9-110">Сведения о подключении нескольких пользователей в рамках общего качества</span><span class="sxs-lookup"><span data-stu-id="7bdf9-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="7bdf9-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="7bdf9-111">Instructions</span></span>

1. <span data-ttu-id="7bdf9-112">В ресурсах > ресурсы > Prefabs папку «проект» путем перетаскивания «NetworkLobby» prefab в иерархии, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="7bdf9-114">При развертывании prefab «NetworkLobby», вы должны увидеть дочерний объект, называется «NetworkRoom.»</span><span class="sxs-lookup"><span data-stu-id="7bdf9-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="7bdf9-115">С его включенным перейдите в панель инспектора и нажмите кнопку «Добавить компонент».</span><span class="sxs-lookup"><span data-stu-id="7bdf9-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="7bdf9-116">Поиск «PhotonView» и добавить компонент.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-116">Search for "PhotonView" and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="7bdf9-118">Создать новый пустой объект игр в иерархии (щелкните правой кнопкой мыши в иерархии и выберите «Empty» в контекстном меню).</span><span class="sxs-lookup"><span data-stu-id="7bdf9-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="7bdf9-119">Настройте расположение x = 0, y = 0, z = 0 и имя объекта «PhotonUser.»</span><span class="sxs-lookup"><span data-stu-id="7bdf9-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="7bdf9-121">Нажмите кнопку «Добавить компонент» и введите «Универсальный Net Sync» и выберите класс универсального Net синхронизации.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-121">Click on the "Add Component" button and type "Generic Net Sync" and select the Generic Net Sync class.</span></span> <span data-ttu-id="7bdf9-122">Как только появится класса, щелкните флажок «User», чтобы включить его.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-122">Once the class appears, click on the "User" check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="7bdf9-124">Снова щелкните «Добавить компонент» введите «Photon View» и выберите представление Photon класс, который отображается в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-124">Again click on "Add Component" and then type "Photon View" and select the Photon View class that appears in the drop down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="7bdf9-126">Теперь щелкните значок в файл для класса универсального Net синхронизации и перетащите его к полю «Наблюдаемая компоненты» Photon представления.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-126">Now click on the File icon in for the Generic Net Sync class, then drag and drop it to the Photon View's "Observed Components" field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="7bdf9-128">Далее необходимо создать как шары, расположенные для представления каждого пользователя, который соединяет общего качества.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-128">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="7bdf9-129">Щелкните правой кнопкой мыши объект «PhotonUser», который вы только что создали, перейдите «трехмерный объект» и нажмите кнопку «"сферы".»</span><span class="sxs-lookup"><span data-stu-id="7bdf9-129">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="7bdf9-130">Это создаст объект игр sphere как дочерний объект PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-130">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="7bdf9-132">Масштабирование сферы до x = 0.06, y = 0.06 ad z = 0.06.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-132">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="7bdf9-134">Перетащите объект игр «PhotonUser» в папке «prefabs» в панели «проект».</span><span class="sxs-lookup"><span data-stu-id="7bdf9-134">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="7bdf9-135">Затем удалите его из сцены.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-135">Then, delete it from the scene.</span></span> <span data-ttu-id="7bdf9-136">Мы создали готового блока, который будет использоваться при создании процесса или создания новых игроков в общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-136">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="7bdf9-138">Примечание: Убедитесь, что игровому объекту успешно скопирован в папку «prefabs» перед его удалением из иерархии.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-138">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="7bdf9-139">Создает новый объект в иерархии (с помощью сходными указаниями, шаг 3) и назовите его «SharedPlayground.»</span><span class="sxs-lookup"><span data-stu-id="7bdf9-139">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="7bdf9-140">Затем нажмите кнопку «Добавить компонент» и выполните поиск «общих сетевых manager» и щелкните его, чтобы добавить компонент универсальный диспетчер сети.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-140">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="7bdf9-141">Смените положение объекта x = 0, y = 0 и z = 0.</span><span class="sxs-lookup"><span data-stu-id="7bdf9-141">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="7bdf9-143">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="7bdf9-143">Congratulations</span></span>

<span data-ttu-id="7bdf9-144">После того как все описанные выше действия выполнены, и процесс сборки завершен, при нажатии кнопку воспроизведения и подключиться к HoloLens 2, вы должны увидеть сферы перемещения при перемещении голове!</span><span class="sxs-lookup"><span data-stu-id="7bdf9-144">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="7bdf9-145">Она будет видна для любого пользователя, который соединяет проекта Unity!</span><span class="sxs-lookup"><span data-stu-id="7bdf9-145">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="7bdf9-146">[Следующий урок. Sharing(Photon) занятие 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="7bdf9-146">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

