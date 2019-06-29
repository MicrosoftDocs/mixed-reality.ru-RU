---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465218"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="2eadf-104">**Подключение нескольких пользователей**</span><span class="sxs-lookup"><span data-stu-id="2eadf-104">**Connecting multiple users**</span></span> 

<span data-ttu-id="2eadf-105">В этом уроке мы узнаем, как для подключения нескольких пользователей в рамках динамической общей работы.</span><span class="sxs-lookup"><span data-stu-id="2eadf-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="2eadf-106">К концу урока вы сможете открыть приложение на нескольких устройствах и аватар, представленный сфера, каждый пользователь, который соединяет представления см. в разделе.</span><span class="sxs-lookup"><span data-stu-id="2eadf-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="2eadf-107">Цели:</span><span class="sxs-lookup"><span data-stu-id="2eadf-107">Objectives:</span></span>

- <span data-ttu-id="2eadf-108">Настройка СОВМЕСТНОЙ в вашем приложении</span><span class="sxs-lookup"><span data-stu-id="2eadf-108">Configure PUN within your application</span></span>
- <span data-ttu-id="2eadf-109">Настройки игрокам</span><span class="sxs-lookup"><span data-stu-id="2eadf-109">Configure players</span></span>
- <span data-ttu-id="2eadf-110">Сведения о подключении нескольких пользователей в рамках общего качества</span><span class="sxs-lookup"><span data-stu-id="2eadf-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="2eadf-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="2eadf-111">Instructions</span></span>

1. <span data-ttu-id="2eadf-112">В ресурсах "->" ресурсы "->" в папку Prefabs «проект» и перетащите drop prefab NetworkLobby в иерархии, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="2eadf-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="2eadf-114">При развертывании NetworkLobby, вы увидите, что называется NetworkRoom дочерний объект.</span><span class="sxs-lookup"><span data-stu-id="2eadf-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="2eadf-115">Перейдите в панель Инспектор NetworkRoom выбран и нажмите кнопку Добавить компонент.</span><span class="sxs-lookup"><span data-stu-id="2eadf-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="2eadf-116">Поиск PhotonView и добавить компонент.</span><span class="sxs-lookup"><span data-stu-id="2eadf-116">Search for PhotonView and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="2eadf-118">Создайте новый пустой объект игр в иерархии.</span><span class="sxs-lookup"><span data-stu-id="2eadf-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="2eadf-119">Щелкните правой кнопкой мыши в иерархии и выберите в контекстном меню пустым.</span><span class="sxs-lookup"><span data-stu-id="2eadf-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="2eadf-120">Настройте расположение x = 0, y = 0, z = 0 и имя объекта, PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="2eadf-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="2eadf-122">Щелкните Добавить компонент и введите универсальный Net синхронизации. Выберите класс универсального Net синхронизации.</span><span class="sxs-lookup"><span data-stu-id="2eadf-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="2eadf-123">Когда класс отображается, щелкните поле пользователя, чтобы включить его.</span><span class="sxs-lookup"><span data-stu-id="2eadf-123">When the class appears, click on the User check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="2eadf-125">Еще раз щелкните Добавить компонент и введите Photon представления.</span><span class="sxs-lookup"><span data-stu-id="2eadf-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="2eadf-126">Выберите представление Photon класс, который отображается в раскрывающемся списке.</span><span class="sxs-lookup"><span data-stu-id="2eadf-126">Select the Photon View class that appears in the drop-down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="2eadf-128">Щелкните значок файла для класса универсального Net синхронизации.</span><span class="sxs-lookup"><span data-stu-id="2eadf-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="2eadf-129">Перетащите и поместите его в представлении Photon наблюдаемая компоненты поля.</span><span class="sxs-lookup"><span data-stu-id="2eadf-129">Drag and drop it in the Photon View's Observed Components field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="2eadf-131">Теперь создадим сфер, для представления каждого пользователя, который соединяет общего качества.</span><span class="sxs-lookup"><span data-stu-id="2eadf-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="2eadf-132">Щелкните правой кнопкой мыши только что созданный объект PhotonUser и scrolldown для «"трехмерный объект и нажмите кнопку сферы".</span><span class="sxs-lookup"><span data-stu-id="2eadf-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="2eadf-133">Это создаст объект игр sphere как дочерний объект PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="2eadf-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="2eadf-135">Масштабирование сферы до x = 0.06, y = 0.06 ad z = 0.06.</span><span class="sxs-lookup"><span data-stu-id="2eadf-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="2eadf-137">Перетащите игровому объекту PhotonUser в папку Prefabs «проект», а затем удалить его из сцены.</span><span class="sxs-lookup"><span data-stu-id="2eadf-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="2eadf-138">Мы создали готового блока, который может использоваться при создании процесса или создания новых игроков в общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="2eadf-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="2eadf-140">Примечание: Убедитесь, что игровому объекту успешно скопирован в папку Prefabs перед его удалением из вашей иерархии.</span><span class="sxs-lookup"><span data-stu-id="2eadf-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="2eadf-141">Создайте новый объект в иерархии, следуя инструкциям в шаге 3 и назовите его SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="2eadf-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="2eadf-142">Затем нажмите кнопку Добавить компонент и поиск общих сетевых manager и щелкните его, чтобы добавить компонент универсальный диспетчер сети.</span><span class="sxs-lookup"><span data-stu-id="2eadf-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="2eadf-143">Смените положение объекта x = 0, y = 0 и z = 0.</span><span class="sxs-lookup"><span data-stu-id="2eadf-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="2eadf-145">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="2eadf-145">Congratulations</span></span>

<span data-ttu-id="2eadf-146">После завершения все описанные выше действия, и процесс сборки также завершена, нажмите кнопку "Воспроизведение" и подключитесь свои две HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2eadf-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="2eadf-147">Вы должны увидеть сферы перемещения при перемещении голове.</span><span class="sxs-lookup"><span data-stu-id="2eadf-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="2eadf-148">Она будет видна для любого пользователя, который соединяет проекта Unity!</span><span class="sxs-lookup"><span data-stu-id="2eadf-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="2eadf-149">[Следующий урок. Sharing(Photon) занятие 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="2eadf-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

