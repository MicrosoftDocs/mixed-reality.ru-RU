---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416015"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="af5f9-104">Синхронизация перемещений общих объектов</span><span class="sxs-lookup"><span data-stu-id="af5f9-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="af5f9-105">На этом занятии будет рассказано о совместном использовании перемещения объектов всех участников сеанса совместной работы могут работать вместе и просмотра взаимодействия других пользователей.</span><span class="sxs-lookup"><span data-stu-id="af5f9-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="af5f9-106">Это занятие основано лунный запуска, который был создан как часть [учебники базового модуля](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="af5f9-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="af5f9-107">Цели:</span><span class="sxs-lookup"><span data-stu-id="af5f9-107">Objectives:</span></span>

- <span data-ttu-id="af5f9-108">Переведет в средстве запуска лунный календарь в качестве трехмерной модели для совместного использования</span><span class="sxs-lookup"><span data-stu-id="af5f9-108">Bring in the Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="af5f9-109">Настройка проекта для совместного использования на перемещение трехмерной модели.</span><span class="sxs-lookup"><span data-stu-id="af5f9-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="af5f9-110">Узнайте, как создать базовое приложение совместной работы нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="af5f9-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="af5f9-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="af5f9-111">Instructions</span></span>

1. <span data-ttu-id="af5f9-112">Сохраните сцены на предыдущем занятии (CTRL + S).</span><span class="sxs-lookup"><span data-stu-id="af5f9-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="af5f9-113">Вы может присвойте ей имя «HLSharedProjectMainPart4.unity», чтобы его было легко найти, когда она понадобится снова.</span><span class="sxs-lookup"><span data-stu-id="af5f9-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="af5f9-114">В окне проекта в ресурсах > папки Scripts двойного щелчка по GenericNetSync, чтобы открыть его в Visual Studio или редактор, при использовании которой когда-либо кода.</span><span class="sxs-lookup"><span data-stu-id="af5f9-114">In the Project window, in the Assets > Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="af5f9-115">В строках, 34 и 38, удалите «/ /» для активации код для таблицы, который будет использоваться на этом занятии.</span><span class="sxs-lookup"><span data-stu-id="af5f9-115">On lines 34 and 38, remove the "//" to activate the code for the Table that we will use in this lesson.</span></span>  <span data-ttu-id="af5f9-116">Затем сохраните файл.</span><span class="sxs-lookup"><span data-stu-id="af5f9-116">Then Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="af5f9-117">В окне проекта дважды щелкните файл PhotonRoom.cs в ресурсах > папку скриптов, чтобы снова открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af5f9-117">In the project window, double click on the PhotonRoom.cs file in the Assets > Scripts folder to again open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="af5f9-118">Так же, как на шаге 3, нам необходимо удалить «/ /» для активации код в строки, 25 и 26, 106.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="af5f9-118">Just like in step 3 we need to remove the "//" to activate the code at lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="af5f9-119">В иерархическом представлении выберите объект NetworkRoom.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="af5f9-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="af5f9-120">В представлении проекта, перейдите к активам > ресурсы > Prefabs.</span><span class="sxs-lookup"><span data-stu-id="af5f9-120">In the project view, navigate to Assets > Resources > Prefabs.</span></span> <span data-ttu-id="af5f9-121">Во-первых путем перетаскивания таблицы prefab в слоте «Tableprefab» в классе PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="af5f9-121">First, drag and drop the Table prefab to the "Tableprefab" slot on the PhotonRoom class.</span></span> <span data-ttu-id="af5f9-122">Затем перетащите и поместите LunarModule prefab «Модуль Prefab» слот в классе PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="af5f9-122">Next drag and drop the LunarModule prefab to the "Module Prefab" slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="af5f9-123">Примечание. Если щелкнуть один из объектов prefab и выпуска, инспектор переключится на этот объект.</span><span class="sxs-lookup"><span data-stu-id="af5f9-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="af5f9-124">Нажмите кнопку, простым перетаскиванием выпуска каждого объекта в его соответствующий разъем.</span><span class="sxs-lookup"><span data-stu-id="af5f9-124">Click, drag, drop and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="af5f9-125">Теперь щелкните стрелку слева от «MixedRealityPlayspace» и вниз игр дочерний объект, «MainCamera» в «SharedPlayground» prefab.</span><span class="sxs-lookup"><span data-stu-id="af5f9-125">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="af5f9-126">Затем удалите prefab «MixedRealityPlayspace» (Чтобы удалить, выберите готового блока и выберите «Удалить» на клавиатуре).</span><span class="sxs-lookup"><span data-stu-id="af5f9-126">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

<span data-ttu-id="af5f9-128">Примечание.  Убедитесь, что задано 0,0,0 SharedPlayground и Main Camera позиций.</span><span class="sxs-lookup"><span data-stu-id="af5f9-128">note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="af5f9-129">Создает новый объект игр установить как дочерний объект к родительскому объекту «SharedPlayground» (Чтобы создать новый объект, щелкните правой кнопкой родительский объект и выберите «создать пустой»).</span><span class="sxs-lookup"><span data-stu-id="af5f9-129">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span> 

10. <span data-ttu-id="af5f9-130">Выбрав новый объект в иерархии измените имя объекта на «TableAnchor» на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="af5f9-130">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="af5f9-131">Кроме того нажмите кнопку «Добавить компонент» и найдите компонент «TableAnchor».</span><span class="sxs-lookup"><span data-stu-id="af5f9-131">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="af5f9-132">Выберите его и добавить его к объекту.</span><span class="sxs-lookup"><span data-stu-id="af5f9-132">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="af5f9-134">Примечание: задать расположение для x = 1 = 0,55 y и z = 2.</span><span class="sxs-lookup"><span data-stu-id="af5f9-134">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="af5f9-135">Кроме того, установите поворот в y = 90.</span><span class="sxs-lookup"><span data-stu-id="af5f9-135">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="af5f9-137">Теперь на панели «проект» в папке «prefabs» перетащите prefab «table» в «TableAnchor» дочерний объект, который вы только что создали.</span><span class="sxs-lookup"><span data-stu-id="af5f9-137">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="af5f9-139">Наконец в объекте «DebugWindow», измените ширину для 80, а высоту — 10.</span><span class="sxs-lookup"><span data-stu-id="af5f9-139">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="af5f9-141">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="af5f9-141">Congratulations</span></span>

<span data-ttu-id="af5f9-142">После завершения этого все пользователи, которые объединяют проекта Unity для перемещения лунный средства запуска.</span><span class="sxs-lookup"><span data-stu-id="af5f9-142">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="af5f9-143">Таким образом, чтобы каждый пользователь будет видеть других пользователей взаимодействий, синхронизируются все перемещения.</span><span class="sxs-lookup"><span data-stu-id="af5f9-143">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="af5f9-144">Эти концепции служат в качестве фундаментальные строительные блоки, полнофункциональную общего совместной работы.</span><span class="sxs-lookup"><span data-stu-id="af5f9-144">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="af5f9-145">Несмотря на то, что все пользователи соединяются как часть общего процесса и можно увидеть относительный перемещения объектов, оно будет по-прежнему не удается точно выровнять аватары и объекты таким образом, чтобы локальные пользователи см. в разделе друг с другом и объектов в том же месте в пределах физическое устройство мир.</span><span class="sxs-lookup"><span data-stu-id="af5f9-145">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="af5f9-146">Чтобы привязать локальные общие ассоциации, каждое устройство требует общее представление о физической среды.</span><span class="sxs-lookup"><span data-stu-id="af5f9-146">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="af5f9-147">В этом модуле, этого можно добиться с помощью [привязки пространственных Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), которые будут реализованы в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="af5f9-147">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="af5f9-148">Перед переходом к следующему занятию, необходимо завершить модуль ASA обучения, который мы рассмотрим основы ASA, требуется учетная запись Azure и создания ресурсов и другие фундаментальные зданий блоки прежде, чем мы можно интегрировать в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="af5f9-148">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="af5f9-149">[Следующий урок. Sharing(Photon) занятие 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="af5f9-149">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

