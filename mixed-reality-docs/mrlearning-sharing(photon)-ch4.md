---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327561"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="0bb55-104">Синхронизация перемещений общих объектов</span><span class="sxs-lookup"><span data-stu-id="0bb55-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="0bb55-105">На этом занятии будет рассказано о совместном использовании перемещения объектов всех участников сеанса совместной работы могут работать вместе и просмотра взаимодействия других пользователей.</span><span class="sxs-lookup"><span data-stu-id="0bb55-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="0bb55-106">Это занятие основано лунный запуска, который был создан как часть [учебники базового модуля](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="0bb55-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="0bb55-107">Цели:</span><span class="sxs-lookup"><span data-stu-id="0bb55-107">Objectives:</span></span>

- <span data-ttu-id="0bb55-108">Импортировать завершенного лунный запуска в виде трехмерной модели для совместного использования</span><span class="sxs-lookup"><span data-stu-id="0bb55-108">Import the completed Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="0bb55-109">Настройка проекта для совместного использования на перемещение трехмерной модели.</span><span class="sxs-lookup"><span data-stu-id="0bb55-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="0bb55-110">Узнайте, как создать базовое приложение совместной работы нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="0bb55-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="0bb55-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0bb55-111">Instructions</span></span>

1. <span data-ttu-id="0bb55-112">Сохраните сцены на предыдущем занятии (CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="0bb55-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="0bb55-113">Вы может присвойте ей имя «HLSharedProjectMainPart4.unity», чтобы его было легко найти, когда она понадобится снова.</span><span class="sxs-lookup"><span data-stu-id="0bb55-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="0bb55-114">Удалите объект «NetworkLobby» (по, выбрав его и нажав клавишу delete).</span><span class="sxs-lookup"><span data-stu-id="0bb55-114">Delete the "NetworkLobby" object (by selecting it and pressing delete).</span></span> <span data-ttu-id="0bb55-115">Кроме того перейдите в папку «prefabs» из занятия 2 и удалить с него prefab «NetworkLobby».</span><span class="sxs-lookup"><span data-stu-id="0bb55-115">Also, go into the "prefabs" folder from lesson 2 and delete the "NetworkLobby" prefab from there as well.</span></span>

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. <span data-ttu-id="0bb55-117">Новый пользовательский пакет (например, шаг 2 на занятии 2) и импорта [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) и [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span><span class="sxs-lookup"><span data-stu-id="0bb55-117">Import a new custom package (like step 2 from the lesson 2) and import the [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) and the [NetworkLobbyReplacement.unitypackage.](linkforNetworklobbyreplacement package here)</span></span>

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. <span data-ttu-id="0bb55-119">Теперь в папке «prefabs» перетащите новый prefab «NetworkLobby» в иерархии.</span><span class="sxs-lookup"><span data-stu-id="0bb55-119">Now, in the "prefabs" folder, drag the new "NetworkLobby" prefab into the hierarchy .</span></span> 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> <span data-ttu-id="0bb55-121">Обратите внимание: два пакета, мы импортировали ранее обновлены prefab «NetworkLobby».</span><span class="sxs-lookup"><span data-stu-id="0bb55-121">note: the two packages we imported in the previous steps updated the "NetworkLobby" prefab.</span></span> <span data-ttu-id="0bb55-122">Избавляет вас от лишней работы по вводу!</span><span class="sxs-lookup"><span data-stu-id="0bb55-122">It saves you from a lot of typing!</span></span>

5. <span data-ttu-id="0bb55-123">Теперь щелкните стрелку слева от «MixedRealityPlayspace» и вниз игр дочерний объект, «MainCamera» в «SharedPlayground» prefab.</span><span class="sxs-lookup"><span data-stu-id="0bb55-123">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="0bb55-124">Затем удалите prefab «MixedRealityPlayspace» (Чтобы удалить, выберите готового блока и выберите «Удалить» на клавиатуре).</span><span class="sxs-lookup"><span data-stu-id="0bb55-124">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. <span data-ttu-id="0bb55-126">Создает новый объект игр установить как дочерний объект к родительскому объекту «SharedPlayground» (Чтобы создать новый объект, щелкните правой кнопкой родительский объект и выберите «создать пустой»).</span><span class="sxs-lookup"><span data-stu-id="0bb55-126">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span>
7. <span data-ttu-id="0bb55-127">Выбрав новый объект в иерархии измените имя объекта на «TableAnchor» на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="0bb55-127">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="0bb55-128">Кроме того нажмите кнопку «Добавить компонент» и найдите компонент «TableAnchor».</span><span class="sxs-lookup"><span data-stu-id="0bb55-128">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="0bb55-129">Выберите его и добавить его к объекту.</span><span class="sxs-lookup"><span data-stu-id="0bb55-129">Select it and add it to the object.</span></span>

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="0bb55-131">Примечание: задать расположение для x = 1 = 0,55 y и z = 2.</span><span class="sxs-lookup"><span data-stu-id="0bb55-131">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="0bb55-132">Кроме того, установите поворот в y = 90.</span><span class="sxs-lookup"><span data-stu-id="0bb55-132">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. <span data-ttu-id="0bb55-134">Теперь на панели «проект» в папке «prefabs» перетащите prefab «table» в «TableAnchor» дочерний объект, который вы только что создали.</span><span class="sxs-lookup"><span data-stu-id="0bb55-134">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. <span data-ttu-id="0bb55-136">Выберите «NetworkRoom», дочерний объект в разделе «NetworkLobby» низкого уровня в иерархии и нажмите кнопку «Добавить компонент» в панели инспектора и найдите «PhotonView» и добавьте скрипт, чтобы "*NetworkRoom*» объект.</span><span class="sxs-lookup"><span data-stu-id="0bb55-136">Select "NetworkRoom," a child object under "NetworkLobby" in the hierachy, and click "add component" in the inspector panel and search for "PhotonView" and add the script to the "*NetworkRoom*" object.</span></span>

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. <span data-ttu-id="0bb55-138">Наконец в объекте «DebugWindow», измените ширину для 80, а высоту — 10.</span><span class="sxs-lookup"><span data-stu-id="0bb55-138">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="0bb55-140">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="0bb55-140">Congratulations</span></span>

<span data-ttu-id="0bb55-141">После завершения этого все пользователи, которые объединяют проекта Unity для перемещения лунный средства запуска.</span><span class="sxs-lookup"><span data-stu-id="0bb55-141">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="0bb55-142">Таким образом, чтобы каждый пользователь будет видеть других пользователей взаимодействий, синхронизируются все перемещения.</span><span class="sxs-lookup"><span data-stu-id="0bb55-142">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="0bb55-143">Эти концепции служат в качестве фундаментальные строительные блоки, полнофункциональную общего совместной работы.</span><span class="sxs-lookup"><span data-stu-id="0bb55-143">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="0bb55-144">Несмотря на то, что все пользователи соединяются как часть общего процесса и можно увидеть относительный перемещения объектов, оно будет по-прежнему не удается точно выровнять аватары и объекты таким образом, чтобы локальные пользователи см. в разделе друг с другом и объектов в том же месте в пределах физическое устройство мир.</span><span class="sxs-lookup"><span data-stu-id="0bb55-144">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="0bb55-145">Чтобы привязать локальные общие ассоциации, каждое устройство требует общее представление о физической среды.</span><span class="sxs-lookup"><span data-stu-id="0bb55-145">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="0bb55-146">В этом модуле, этого можно добиться с помощью [привязки пространственных Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), которые будут реализованы в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="0bb55-146">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="0bb55-147">Перед переходом к следующему занятию, необходимо завершить модуль ASA обучения, который мы рассмотрим основы ASA, требуется учетная запись Azure и создания ресурсов и другие фундаментальные зданий блоки прежде, чем мы можно интегрировать в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="0bb55-147">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="0bb55-148">[Следующий урок. Sharing(Photon) занятие 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="0bb55-148">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

