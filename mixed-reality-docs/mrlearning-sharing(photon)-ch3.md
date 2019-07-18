---
title: Модуль совместного использования MR для HoloLens 2
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 92bea1f3130f67645c10e36fe40cd4bc6f8b9151
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293658"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="26315-104">Подключение нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="26315-104">Connecting multiple users</span></span>

<span data-ttu-id="26315-105">На этом занятии мы научитесь подключать нескольких пользователей в рамках совместного использования.</span><span class="sxs-lookup"><span data-stu-id="26315-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="26315-106">К концу этого занятия вы сможете открыть приложение на нескольких устройствах и увидеть аватар, представленный сферой, представления каждого из пользователей, которые присоединяются к.</span><span class="sxs-lookup"><span data-stu-id="26315-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="26315-107">Служит</span><span class="sxs-lookup"><span data-stu-id="26315-107">Objectives:</span></span>

- <span data-ttu-id="26315-108">Настройка шутка в приложении</span><span class="sxs-lookup"><span data-stu-id="26315-108">Configure PUN within your application</span></span>
- <span data-ttu-id="26315-109">Настройка игроков</span><span class="sxs-lookup"><span data-stu-id="26315-109">Configure players</span></span>
- <span data-ttu-id="26315-110">Узнайте, как подключить нескольких пользователей в общем интерфейсе</span><span class="sxs-lookup"><span data-stu-id="26315-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="26315-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="26315-111">Instructions</span></span>

1. <span data-ttu-id="26315-112">В папке Assets-> Resources-> Prefabs на панели проекта перетащите Нетворклобби prefab в иерархию, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="26315-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="26315-114">При развертывании Нетворклобби вы увидите дочерний объект с именем Нетворкрум.</span><span class="sxs-lookup"><span data-stu-id="26315-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="26315-115">Выбрав Нетворкрум, перейдите на панель инспектора и нажмите кнопку Добавить компонент.</span><span class="sxs-lookup"><span data-stu-id="26315-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="26315-116">Выполните поиск Фотонвиев и добавьте компонент.</span><span class="sxs-lookup"><span data-stu-id="26315-116">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="26315-118">Создание нового пустого игрового объекта в иерархии.</span><span class="sxs-lookup"><span data-stu-id="26315-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="26315-119">Щелкните правой кнопкой мыши в иерархии и выберите в контекстном меню пункт Очистить.</span><span class="sxs-lookup"><span data-stu-id="26315-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="26315-120">Убедитесь, что для положения задано значение x = 0, y = 0, z = 0 и имя объекта Фотонусер.</span><span class="sxs-lookup"><span data-stu-id="26315-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="26315-122">Щелкните Добавить компонент и введите Общая NET Sync. Выберите универсальный класс NET Sync.</span><span class="sxs-lookup"><span data-stu-id="26315-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="26315-123">Когда появится класс, установите флажок Пользователь, чтобы включить его.</span><span class="sxs-lookup"><span data-stu-id="26315-123">When the class appears, click on the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="26315-125">Снова щелкните Добавить компонент и введите Photon View.</span><span class="sxs-lookup"><span data-stu-id="26315-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="26315-126">Выберите класс представления Photon, который появится в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="26315-126">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="26315-128">Щелкните значок файла для универсального класса NET Sync.</span><span class="sxs-lookup"><span data-stu-id="26315-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="26315-129">Перетащите его в поле наблюдаемые компоненты представления Photon.</span><span class="sxs-lookup"><span data-stu-id="26315-129">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="26315-131">Далее мы создадим шарик для представления каждого человека, который присоединяется к общему интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="26315-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="26315-132">Щелкните правой кнопкой мыши объект Фотонусер, который вы только что создали, и скроллдовн в «3D Object» и щелкните «Sphere».</span><span class="sxs-lookup"><span data-stu-id="26315-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="26315-133">В результате будет создан объект игры сферы в качестве дочернего объекта для объекта Фотонусер.</span><span class="sxs-lookup"><span data-stu-id="26315-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="26315-135">Масштабировать сферу до x = 0.06, y = 0.06, AD z = 0.06.</span><span class="sxs-lookup"><span data-stu-id="26315-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="26315-137">Перетащите объект Game Фотонусер в папку Prefabs на панели проект, а затем удалите ее из сцены.</span><span class="sxs-lookup"><span data-stu-id="26315-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="26315-138">Теперь мы создали prefab, который можно использовать при создании новых игроков, а также для создания экземпляров в общем интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="26315-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="26315-140">Примечание. Убедитесь, что объект Game успешно скопирован в папку Prefabs перед удалением из иерархии.</span><span class="sxs-lookup"><span data-stu-id="26315-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="26315-141">Создайте новый объект в иерархии, следуя инструкциям, приведенным в шаге 3, и назовите его Шаредплайграунд.</span><span class="sxs-lookup"><span data-stu-id="26315-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="26315-142">Затем нажмите кнопку Добавить компонент, найдите общий диспетчер сети и щелкните его, чтобы добавить общий компонент диспетчера сети.</span><span class="sxs-lookup"><span data-stu-id="26315-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="26315-143">Измените расположение объекта на x = 0, y = 0 и z = 0.</span><span class="sxs-lookup"><span data-stu-id="26315-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="26315-145">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="26315-145">Congratulations</span></span>

<span data-ttu-id="26315-146">После выполнения всех описанных выше действий и завершения процесса сборки нажмите кнопку Воспроизвести и подключите HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="26315-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="26315-147">При перемещении головного подразделения вы должны увидеть сферу движения.</span><span class="sxs-lookup"><span data-stu-id="26315-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="26315-148">Это будет показано для любого пользователя, который присоединяется к проекту Unity!</span><span class="sxs-lookup"><span data-stu-id="26315-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="26315-149">[Следующий урок. Общий доступ (Photon) Урок 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="26315-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

