---
title: Учебники по возможностям для нескольких пользователей — 4. Совместное использование передвижений объектов несколькими пользователями
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 56f7c767323285453cbeea9034f97a7c14e92359
ms.sourcegitcommit: d73d9012941fa1b13eb7d2f45ccc481d6365827a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885634"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="0055b-105">4. Совместное использование передвижений объектов несколькими пользователями</span><span class="sxs-lookup"><span data-stu-id="0055b-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="0055b-106">В этом руководстве вы узнаете, как совместно использовать перемещения объектов, чтобы все участники общего сеанса могли совместно работать и просматривать взаимодействия друг с другом.</span><span class="sxs-lookup"><span data-stu-id="0055b-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="0055b-107">Это занятие строится на основе лунного модуля запуска, созданного в рамках [учебников по базовому модулю](mrlearning-base.md).</span><span class="sxs-lookup"><span data-stu-id="0055b-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="0055b-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="0055b-108">Objectives</span></span>

- <span data-ttu-id="0055b-109">Подключите Лунный модуль запуска к совместно используемой трехмерной модели.</span><span class="sxs-lookup"><span data-stu-id="0055b-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="0055b-110">Настройка проекта для совместного использования перемещений трехмерной модели</span><span class="sxs-lookup"><span data-stu-id="0055b-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="0055b-111">Узнайте, как создать базовое многопользовательское приложение для совместной работы</span><span class="sxs-lookup"><span data-stu-id="0055b-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="0055b-112">Инструкция</span><span class="sxs-lookup"><span data-stu-id="0055b-112">Instructions</span></span>

1. <span data-ttu-id="0055b-113">Сохраните сцену из предыдущего занятия (Control + S).</span><span class="sxs-lookup"><span data-stu-id="0055b-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="0055b-114">Можно присвоить ему имя HLSharedProjectMainPart4. Unity, чтобы его было проще найти по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="0055b-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="0055b-115">В окне проекта в папке Assets-> Scripts дважды щелкните Женерикнетсинк, чтобы открыть его в Visual Studio или в любом редакторе кода, который вы используете.</span><span class="sxs-lookup"><span data-stu-id="0055b-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="0055b-117">В строках 34 и 38 удалите "//", чтобы активировать код для таблицы, которая будет использоваться на этом занятии.</span><span class="sxs-lookup"><span data-stu-id="0055b-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="0055b-118">Затем сохраните файл.</span><span class="sxs-lookup"><span data-stu-id="0055b-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="0055b-120">В окне проекта дважды щелкните файл PhotonRoom.cs в папке Assets-> Scripts, чтобы открыть его в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0055b-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="0055b-122">Как и на шаге 3, необходимо удалить "//", чтобы активировать код в строках 25, 26 и 106.</span><span class="sxs-lookup"><span data-stu-id="0055b-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="0055b-125">В представлении Иерархия выберите объект Нетворкрум.</span><span class="sxs-lookup"><span data-stu-id="0055b-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="0055b-127">В представлении проекта перейдите к разделу Assets-> Resources-> Prefabs.</span><span class="sxs-lookup"><span data-stu-id="0055b-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="0055b-128">Сначала перетащите таблицу prefab в слот Таблепрефаб в классе Фотонрум.</span><span class="sxs-lookup"><span data-stu-id="0055b-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="0055b-129">Затем перетащите Роккетлаунчеркомплетевариантпрефаб в гнездо Module prefab в классе Фотонрум.</span><span class="sxs-lookup"><span data-stu-id="0055b-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="0055b-131">Если щелкнуть один из объектов prefab и выпустить, инспектор будет переключаться на этот объект.</span><span class="sxs-lookup"><span data-stu-id="0055b-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="0055b-132">Щелкните, перетащите, удалите и выпустите каждый объект в соответствующем слоте.</span><span class="sxs-lookup"><span data-stu-id="0055b-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="0055b-133">Щелкните стрелку слева от Микседреалитиплайспаце и переместите дочерний объект Game Маинкамера в Шаредплайграунд prefab.</span><span class="sxs-lookup"><span data-stu-id="0055b-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="0055b-134">Затем удалите prefab, Микседреалитиплайспаце, выбрав prefab и нажав кнопку "Удалить" на клавиатуре.</span><span class="sxs-lookup"><span data-stu-id="0055b-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="0055b-136">Убедитесь, что значения основной камеры и Шаредплайграунд установлены равными 0, 0, 0.</span><span class="sxs-lookup"><span data-stu-id="0055b-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="0055b-137">Выберите объект "Шаредплайграунд" и щелкните правой кнопкой мыши, чтобы выбрать команду "создать пустой", чтобы создать пустой объект Game в качестве дочернего объекта игры "Шаредплайграунд".</span><span class="sxs-lookup"><span data-stu-id="0055b-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="0055b-139">С помощью нового объекта, выбранного в иерархии, измените имя объекта на Таблеанчор на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="0055b-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="0055b-140">Кроме того, нажмите кнопку Добавить компонент и найдите компонент Таблеанчор.</span><span class="sxs-lookup"><span data-stu-id="0055b-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="0055b-141">Выберите его и добавьте в объект.</span><span class="sxs-lookup"><span data-stu-id="0055b-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="0055b-143">На панели проект в папке Prefabs перетащите таблицу prefab в только что созданный дочерний объект "Таблеанчор".</span><span class="sxs-lookup"><span data-stu-id="0055b-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)
   
12. <span data-ttu-id="0055b-145">Откройте prefab Resources-> Rocket Launcher_Complete Variant > ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0055b-145">Open the "Rocket Launcher_Complete Variant" prefab from Assets->Resources->Prefabs.</span></span>

13. <span data-ttu-id="0055b-146">Выберите GameObject "Лунармодуле" и добавьте следующие два компонента: "Photon преобразование View" и "Photon View".</span><span class="sxs-lookup"><span data-stu-id="0055b-146">Select the "LunarModule" GameObject and add the following two components: "Photon Transform View" and "Photon View".</span></span>

14. <span data-ttu-id="0055b-147">Выбрав GameObject "Лунармодуле", перетащите компонент "представление преобразования Photon" в гнездо "наблюдаемые компоненты" в компоненте "представление" Photon ".</span><span class="sxs-lookup"><span data-stu-id="0055b-147">With the "LunarModule" GameObject still selected, drag the "Photon Transform View" component into the "Observed Components" slot in the "Photon View" component.</span></span>

## <a name="congratulations"></a><span data-ttu-id="0055b-148">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="0055b-148">Congratulations</span></span>

<span data-ttu-id="0055b-149">Когда это будет завершено, найдите подсвой Лунный модуль.</span><span class="sxs-lookup"><span data-stu-id="0055b-149">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="0055b-150">После этого все пользователи, присоединенные к проекту Unity, могут переместить Лунный модуль запуска.</span><span class="sxs-lookup"><span data-stu-id="0055b-150">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="0055b-151">Все перемещения синхронизируются таким образом, чтобы каждый пользователь мог видеть взаимодействия друг с другом.</span><span class="sxs-lookup"><span data-stu-id="0055b-151">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="0055b-152">Эти понятия служат в качестве основных стандартных блоков для полнофункциональных общих возможностей совместной работы.</span><span class="sxs-lookup"><span data-stu-id="0055b-152">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="0055b-153">Несмотря на то что все пользователи подключены как часть общего интерфейса и могут видеть относительные перемещения объектов, приложение по-прежнему не может точно расположить аватары и объекты, чтобы локальные пользователи не могли видеть друг друга и объекты в том же месте в физический мир.</span><span class="sxs-lookup"><span data-stu-id="0055b-153">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="0055b-154">Чтобы привязать локальные общие интерфейсы, каждому устройству требуется общее понимание физической среды.</span><span class="sxs-lookup"><span data-stu-id="0055b-154">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="0055b-155">В этом модуле это достигается с помощью [пространственных привязок Azure](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA), которые будут реализованы на следующем занятии.</span><span class="sxs-lookup"><span data-stu-id="0055b-155">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="0055b-156">Прежде чем перейти к следующему занятию, необходимо завершить работу модуля ASA Learning, который охватывает основы ASA, учетную запись Azure и создание ресурсов, а также другие фундаментальные блоки зданий, необходимые, прежде чем мы сможем интегрировать это в наш общий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="0055b-156">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="0055b-157">[Следующее занятие: 5. Интеграция пространственных привязок Azure в общий интерфейс](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="0055b-157">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
