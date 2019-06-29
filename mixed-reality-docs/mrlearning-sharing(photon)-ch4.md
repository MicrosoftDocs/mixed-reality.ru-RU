---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b729de818dfa21df8fbce782a24a611a365ac795
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465226"
---
# <a name="synchronizing-shared-object-movements"></a><span data-ttu-id="d597c-104">Синхронизация общий объект перемещения</span><span class="sxs-lookup"><span data-stu-id="d597c-104">Synchronizing shared object movements</span></span>

<span data-ttu-id="d597c-105">В этом уроке мы узнаем, как совместно использовать перемещения объектов всех участников сеанса совместной работы могут работать вместе и просмотра взаимодействия других пользователей.</span><span class="sxs-lookup"><span data-stu-id="d597c-105">In this lesson, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="d597c-106">Это занятие основано лунный запуска, который был создан как часть [учебники базового модуля](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="d597c-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="d597c-107">Цели:</span><span class="sxs-lookup"><span data-stu-id="d597c-107">Objectives:</span></span>

- <span data-ttu-id="d597c-108">Переведет в средстве запуска лунный календарь в качестве трехмерной модели для совместного использования</span><span class="sxs-lookup"><span data-stu-id="d597c-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="d597c-109">Настройка проекта для совместного использования на перемещение трехмерной модели.</span><span class="sxs-lookup"><span data-stu-id="d597c-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="d597c-110">Узнайте, как создать базовое приложение совместной работы нескольких пользователей</span><span class="sxs-lookup"><span data-stu-id="d597c-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="d597c-111">Инструкция</span><span class="sxs-lookup"><span data-stu-id="d597c-111">Instructions</span></span>


1. <span data-ttu-id="d597c-112">Сохраните сцены на предыдущем занятии (CTRL + + S).</span><span class="sxs-lookup"><span data-stu-id="d597c-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="d597c-113">Вы можете назвать приложение HLSharedProjectMainPart4.unity, чтобы его было легко найти, когда это необходимо.</span><span class="sxs-lookup"><span data-stu-id="d597c-113">You can name it HLSharedProjectMainPart4.unity so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="d597c-114">В окне проекта в ресурсах "->" в папку Scripts, дважды щелкните GenericNetSync, чтобы открыть его в Visual Studio или какой-либо код редактора, которую вы используете.</span><span class="sxs-lookup"><span data-stu-id="d597c-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="d597c-115">Удалите на 34 строк и 38, / / чтобы активировать код для таблицы, который будет использоваться на этом занятии.</span><span class="sxs-lookup"><span data-stu-id="d597c-115">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="d597c-116">затем сохраните файл.</span><span class="sxs-lookup"><span data-stu-id="d597c-116">next, Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="d597c-117">В окне проекта дважды щелкните файл PhotonRoom.cs в ресурсах "->" папку скриптов, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d597c-117">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="d597c-118">Так же, как на шаге 3, нам необходимо удалить / / чтобы активировать код в строки, 25 и 26, 106.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="d597c-118">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="d597c-119">В иерархическом представлении выберите объект NetworkRoom.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="d597c-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="d597c-120">В представлении проекта, перейдите в раздел ресурсов "->" ресурсы "->" Prefabs.</span><span class="sxs-lookup"><span data-stu-id="d597c-120">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="d597c-121">Во-первых путем перетаскивания таблицы prefab слот Tableprefab PhotonRoom класса.</span><span class="sxs-lookup"><span data-stu-id="d597c-121">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="d597c-122">Затем перетащите и поместите LunarModule prefab модуль Prefab слот в классе PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="d597c-122">Next drag and drop the LunarModule prefab to the Module Prefab slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="d597c-123">Примечание. Если щелкнуть один из объектов prefab и выпуска, инспектор переключится на этот объект.</span><span class="sxs-lookup"><span data-stu-id="d597c-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="d597c-124">Щелкните, drop и перетащите выпуска каждого объекта в его соответствующий разъем.</span><span class="sxs-lookup"><span data-stu-id="d597c-124">Click, drag, drop, and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="d597c-125">Щелкните стрелку слева от MixedRealityPlayspace и вниз игр дочерний объект, MainCamera в SharedPlayground prefab.</span><span class="sxs-lookup"><span data-stu-id="d597c-125">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="d597c-126">Затем удалите готового блока, MixedRealityPlayspace удалить готового блока и выберите «Удалить» на клавиатуре).</span><span class="sxs-lookup"><span data-stu-id="d597c-126">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="d597c-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="d597c-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

<span data-ttu-id="d597c-128">Примечание.  Убедитесь, что задано 0,0,0 SharedPlayground и Main Camera позиций.</span><span class="sxs-lookup"><span data-stu-id="d597c-128">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="d597c-129">Создание игр объекта значение как дочерний объект SharedPlayground родительский объект для создания нового объекта.</span><span class="sxs-lookup"><span data-stu-id="d597c-129">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="d597c-130">Щелкните правой кнопкой мыши в родительском объекте и выберите создать пустой.</span><span class="sxs-lookup"><span data-stu-id="d597c-130">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="d597c-131">Выбрав новый объект в иерархии измените имя объекта на TableAnchor панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="d597c-131">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="d597c-132">Кроме того выберите Добавить компонент и поиск TableAnchor компонента.</span><span class="sxs-lookup"><span data-stu-id="d597c-132">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="d597c-133">Выберите его и добавить его к объекту.</span><span class="sxs-lookup"><span data-stu-id="d597c-133">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="d597c-135">Примечание. Задать расположение для x = 1 = 0,55 y и z = 2.</span><span class="sxs-lookup"><span data-stu-id="d597c-135">Note: Set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="d597c-136">Кроме того, установите поворот в y = 90.</span><span class="sxs-lookup"><span data-stu-id="d597c-136">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="d597c-138">Теперь из панели «проект» в папку Prefabs перетащите prefab таблицы в только что созданный дочерний объект «TableAnchor».</span><span class="sxs-lookup"><span data-stu-id="d597c-138">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="d597c-140">Наконец в объекте DebugWindow измените ширину для 80, а высоту — 10.</span><span class="sxs-lookup"><span data-stu-id="d597c-140">Finally, in the DebugWindow object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="d597c-142">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d597c-142">Congratulations</span></span>


<span data-ttu-id="d597c-143">После завершения этого все пользователи, которые объединяют проекта Unity для перемещения лунный средства запуска.</span><span class="sxs-lookup"><span data-stu-id="d597c-143">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="d597c-144">Таким образом, чтобы каждый пользователь будет видеть других пользователей взаимодействий, синхронизируются все перемещения.</span><span class="sxs-lookup"><span data-stu-id="d597c-144">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="d597c-145">Эти концепции служат в качестве фундаментальные строительные блоки, полнофункциональный и ту же общую совместной работы.</span><span class="sxs-lookup"><span data-stu-id="d597c-145">These concepts serve as the foundational building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="d597c-146">Несмотря на то, что все пользователи соединяются как часть общего процесса и можно увидеть относительный перемещения объектов, оно будет по-прежнему не удается точно выровнять аватары и объекты таким образом, чтобы локальные пользователи см. в разделе друг с другом и объектов в том же месте в пределах физическое устройство мир.</span><span class="sxs-lookup"><span data-stu-id="d597c-146">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="d597c-147">Чтобы привязать локальные общие ассоциации, каждое устройство требует общее представление о физической среды.</span><span class="sxs-lookup"><span data-stu-id="d597c-147">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="d597c-148">В этом модуле будет это делается с помощью [привязки пространственных Azure](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), будет реализована в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="d597c-148">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="d597c-149">Прежде чем переходить к следующему занятию, нам потребуется для выполнения модуля обучения ASA, который рассматривает базовые вопросы ASA, требуется учетная запись Azure и создания ресурсов и другие фундаментальные зданий блоки прежде, чем мы можно интегрировать в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d597c-149">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="d597c-150">[Следующий урок. Sharing(Photon) занятие 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="d597c-150">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

