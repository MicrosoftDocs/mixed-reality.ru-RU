---
title: Учебники по возможностям для нескольких пользователей — 3. Подключение нескольких пользователей
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 9441cf7a9685b8a197bab1116202db4a9b026f2e
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334303"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="1f256-105">3. Подключение нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="1f256-105">3. Connecting multiple users</span></span>

<span data-ttu-id="1f256-106">На этом занятии мы научитесь подключать нескольких пользователей в рамках совместного использования.</span><span class="sxs-lookup"><span data-stu-id="1f256-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="1f256-107">К концу этого занятия вы сможете открыть приложение на нескольких устройствах и увидеть аватар, представленный сферой для каждого пользователя, который присоединяется.</span><span class="sxs-lookup"><span data-stu-id="1f256-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="1f256-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="1f256-108">Objectives</span></span>

* <span data-ttu-id="1f256-109">Настройка шутка в приложении</span><span class="sxs-lookup"><span data-stu-id="1f256-109">Configure PUN within your application</span></span>
* <span data-ttu-id="1f256-110">Настройка игроков</span><span class="sxs-lookup"><span data-stu-id="1f256-110">Configure players</span></span>
* <span data-ttu-id="1f256-111">Узнайте, как подключить нескольких пользователей в общем интерфейсе</span><span class="sxs-lookup"><span data-stu-id="1f256-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="1f256-112">Инструкция</span><span class="sxs-lookup"><span data-stu-id="1f256-112">Instructions</span></span>

1. <span data-ttu-id="1f256-113">В папке Assets-> Resources-> Prefabs на панели проекта перетащите Нетворклобби prefab в иерархию, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="1f256-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="1f256-115">При развертывании Нетворклобби вы увидите дочерний объект с именем Нетворкрум.</span><span class="sxs-lookup"><span data-stu-id="1f256-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="1f256-116">Выбрав Нетворкрум, перейдите на панель инспектора и нажмите кнопку Добавить компонент.</span><span class="sxs-lookup"><span data-stu-id="1f256-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="1f256-117">Выполните поиск Фотонвиев и добавьте компонент.</span><span class="sxs-lookup"><span data-stu-id="1f256-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="1f256-119">Создание нового пустого игрового объекта в иерархии.</span><span class="sxs-lookup"><span data-stu-id="1f256-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="1f256-120">Щелкните правой кнопкой мыши иерархию и выберите в контекстном меню пункт Очистить.</span><span class="sxs-lookup"><span data-stu-id="1f256-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="1f256-121">Убедитесь, что для положения задано значение x = 0, y = 0, z = 0 и имя объекта Фотонусер.</span><span class="sxs-lookup"><span data-stu-id="1f256-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="1f256-123">Щелкните Добавить компонент и введите Общая NET Sync. Выберите универсальный класс NET Sync.</span><span class="sxs-lookup"><span data-stu-id="1f256-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="1f256-124">Когда появится класс, установите флажок Пользователь, чтобы включить его.</span><span class="sxs-lookup"><span data-stu-id="1f256-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="1f256-126">Снова нажмите кнопку Добавить компонент и введите Photon View.</span><span class="sxs-lookup"><span data-stu-id="1f256-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="1f256-127">Выберите класс представления Photon, который появится в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="1f256-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="1f256-129">Щелкните значок файла для универсального класса NET Sync.</span><span class="sxs-lookup"><span data-stu-id="1f256-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="1f256-130">Перетащите его в поле наблюдаемые компоненты представления Photon.</span><span class="sxs-lookup"><span data-stu-id="1f256-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="1f256-132">Далее мы создадим шарик для представления каждого человека, который присоединяется к общему интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="1f256-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="1f256-133">Щелкните правой кнопкой мыши объект Фотонусер, который вы только что создали, прокрутите вниз до пункта "трехмерный объект и щелкните" шар ".</span><span class="sxs-lookup"><span data-stu-id="1f256-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="1f256-134">В результате будет создан объект игры сферы в качестве дочернего объекта для объекта Фотонусер.</span><span class="sxs-lookup"><span data-stu-id="1f256-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="1f256-136">Масштабировать сферу до x = 0.06, y = 0.06, AD z = 0.06.</span><span class="sxs-lookup"><span data-stu-id="1f256-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="1f256-138">Перетащите объект Game Фотонусер в папку Prefabs на панели проекта, а затем удалите ее из сцены.</span><span class="sxs-lookup"><span data-stu-id="1f256-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="1f256-139">Теперь вы создали prefab, который можно использовать при создании новых игроков, а также для создания экземпляров в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="1f256-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="1f256-141">Убедитесь, что объект Game успешно скопирован в папку Prefabs, прежде чем удалять его из иерархии.</span><span class="sxs-lookup"><span data-stu-id="1f256-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="1f256-142">Создайте новый объект в иерархии, следуя инструкциям, приведенным в шаге 3, и назовите его Шаредплайграунд.</span><span class="sxs-lookup"><span data-stu-id="1f256-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="1f256-143">Затем нажмите кнопку Добавить компонент и найдите общий диспетчер сети.</span><span class="sxs-lookup"><span data-stu-id="1f256-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="1f256-144">Щелкните его еще раз, чтобы добавить общий компонент диспетчера сети.</span><span class="sxs-lookup"><span data-stu-id="1f256-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="1f256-145">Измените расположение объекта на x = 0, y = 0 и z = 0.</span><span class="sxs-lookup"><span data-stu-id="1f256-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="1f256-147">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="1f256-147">Congratulations</span></span>

<span data-ttu-id="1f256-148">После выполнения всех описанных выше действий, а также завершения процесса сборки нажмите кнопку Воспроизвести и подключите HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1f256-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="1f256-149">При перемещении головного подразделения вы должны увидеть сферу движения.</span><span class="sxs-lookup"><span data-stu-id="1f256-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="1f256-150">Это будет показано для любого пользователя, который присоединяется к проекту Unity!</span><span class="sxs-lookup"><span data-stu-id="1f256-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="1f256-151">[Следующее занятие: 4. Совместное использование передвижений объектов несколькими пользователями](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="1f256-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>
