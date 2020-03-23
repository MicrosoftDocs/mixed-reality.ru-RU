---
title: Руководства по многопользовательским возможностям, часть 4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031247"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="63a06-105">4. Предоставление общего доступа к сведениям о перемещении объекта нескольким пользователям</span><span class="sxs-lookup"><span data-stu-id="63a06-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="63a06-106">В этом руководстве вы узнаете, как совместно использовать перемещения объектов, чтобы все участники общего сеанса могли взаимодействовать друг с другом и наблюдать эти взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="63a06-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="63a06-107">Этот урок основан на проекте лунного модуля, который вы создали при работе с [базовым модулем](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="63a06-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="63a06-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="63a06-108">Objectives</span></span>

- <span data-ttu-id="63a06-109">Подключение лунного модуля в качестве трехмерной модели для совместного использования</span><span class="sxs-lookup"><span data-stu-id="63a06-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="63a06-110">Настройка проекта для совместного использования перемещений трехмерной модели</span><span class="sxs-lookup"><span data-stu-id="63a06-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="63a06-111">Создание простого многопользовательского приложения для совместной работы</span><span class="sxs-lookup"><span data-stu-id="63a06-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="63a06-112">Инструкции</span><span class="sxs-lookup"><span data-stu-id="63a06-112">Instructions</span></span>

1. <span data-ttu-id="63a06-113">Сохраните сцену из предыдущего урока (сочетанием клавиш Ctrl+S).</span><span class="sxs-lookup"><span data-stu-id="63a06-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="63a06-114">Присвойте ей удобное имя, например HLSharedProjectMainPart4.unity, чтобы было проще найти ее, когда она потребуется.</span><span class="sxs-lookup"><span data-stu-id="63a06-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="63a06-115">В окне проекта в папке Assets (Активы) -> Scripts (Скрипты) дважды щелкните GenericNetSync, чтобы открыть его в Visual Studio или в другом редакторе кода, который вы используете.</span><span class="sxs-lookup"><span data-stu-id="63a06-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="63a06-117">В строках 34 и 38 удалите символы "//", чтобы активировать код для стола, который вам потребуется в этом уроке.</span><span class="sxs-lookup"><span data-stu-id="63a06-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="63a06-118">Теперь сохраните этот файл.</span><span class="sxs-lookup"><span data-stu-id="63a06-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="63a06-120">В окне проекта дважды щелкните файл PhotonRoom.cs в папке Assets (Активы) -> Scripts (Скрипты), чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63a06-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="63a06-122">Как и на шаге 3, нам нужно удалить символы "//", чтобы активировать код в строках 25, 26 и 106.</span><span class="sxs-lookup"><span data-stu-id="63a06-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="63a06-125">В представлении Hierarchy (Иерархия) выберите объект NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="63a06-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="63a06-127">В представлении проекта перейдите к папке Assets (Активы) -> Resources (Ресурсы) -> Prefabs (Заготовки).</span><span class="sxs-lookup"><span data-stu-id="63a06-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="63a06-128">Сначала перетащите заготовку Table в слот Tableprefab класса PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="63a06-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="63a06-129">Затем перетащите заготовку RocketLauncherCompleteVariantprefab в слот Module Prefab класса PhotonRoom.</span><span class="sxs-lookup"><span data-stu-id="63a06-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="63a06-131">Если щелкнуть один из объектов заготовки и отпустить кнопку мыши, инспектор переключится на этот объект.</span><span class="sxs-lookup"><span data-stu-id="63a06-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="63a06-132">Поочередно щелкните каждый объект, перетащите его к соответствующему слоту и отпустите.</span><span class="sxs-lookup"><span data-stu-id="63a06-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="63a06-133">Щелкните стрелку слева от MixedRealityPlayspace и переместите дочерний игровой объект MainCamera в заготовку SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="63a06-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="63a06-134">Затем удалите заготовку MixedRealityPlayspace, выбрав ее вышью и нажав клавишу Delete (Удалить) на клавиатуре.</span><span class="sxs-lookup"><span data-stu-id="63a06-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="63a06-136">Убедитесь, что для объектов MainCamera и SharedPlayground установлены положения с координатами 0, 0, 0.</span><span class="sxs-lookup"><span data-stu-id="63a06-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="63a06-137">Выберите объект SharedPlayground и щелкните его правой кнопкой мыши, чтобы выбрать команду create empty (Создать пустой) и создать игровой объект в качестве дочернего для игрового объекта SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="63a06-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="63a06-139">Сохраняя новый объект выделенным в иерархии, на панели Inspector (Инспектор) измените имя объекта на TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="63a06-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="63a06-140">Также щелкните Add Component (Добавить компонент) и найдите компонент TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="63a06-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="63a06-141">Выберите его и добавьте в объект.</span><span class="sxs-lookup"><span data-stu-id="63a06-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="63a06-143">На панели проекта из папки Prefabs (Заготовки) перетащите заготовку Table в только что созданный дочерний объект TableAnchor.</span><span class="sxs-lookup"><span data-stu-id="63a06-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a><span data-ttu-id="63a06-145">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="63a06-145">Congratulations</span></span>

<span data-ttu-id="63a06-146">Завершив эти действия, осмотритесь по сторонам и найдите лунный модуль.</span><span class="sxs-lookup"><span data-stu-id="63a06-146">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="63a06-147">Теперь все пользователи, присоединенные к проекту Unity, могут перемещать лунный модуль по сцене.</span><span class="sxs-lookup"><span data-stu-id="63a06-147">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="63a06-148">Все движения синхронизируются так, что каждый пользователь может наблюдать взаимодействия других пользователей.</span><span class="sxs-lookup"><span data-stu-id="63a06-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="63a06-149">Эта концепция станет базовым строительным элементом для создания полнофункциональных взаимодействий с поддержкой совместной работы.</span><span class="sxs-lookup"><span data-stu-id="63a06-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="63a06-150">Хотя все пользователи подключаются к совместному взаимодействию и видят относительные перемещения объектов, приложение пока не умеет правильно совмещать аватары с объектами, а значит, локальные пользователи будут видеть друг друга и игровые объекты в разных местах реального мира.</span><span class="sxs-lookup"><span data-stu-id="63a06-150">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="63a06-151">Чтобы привязать взаимодействия к локальной среде, каждое устройство должно иметь единое представление о физическом окружении.</span><span class="sxs-lookup"><span data-stu-id="63a06-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="63a06-152">В этом модуле мы применим для этой цели [Пространственные привязки Azure](<https://azure.microsoft.com//services/spatial-anchors/>), которые и реализуем в следующем уроке.</span><span class="sxs-lookup"><span data-stu-id="63a06-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="63a06-153">Прежде чем переходить к следующему уроку, следует выполнить обучающий модуль по Пространственным привязкам Azure, где описаны основные понятия, создание учетной записи и ресурсов Azure и другие важные элементы, которые потребуются нам при интеграции этой возможности в совместное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="63a06-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="63a06-154">[Следующий урок. 5. Интеграция Пространственных привязок Azure в общий интерфейс](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="63a06-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
