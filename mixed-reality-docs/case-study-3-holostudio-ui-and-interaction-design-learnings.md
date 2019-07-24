---
title: Пример использования — 3 Холостудио пользовательского интерфейса и проектирования взаимодействия
description: Сведения о разработке пользовательского интерфейса Холостудио и взаимодействия
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Холостудио, Windows Mixed Reality
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974828"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="0e5b6-104">Пример использования — 3 Холостудио пользовательского интерфейса и проектирования взаимодействия</span><span class="sxs-lookup"><span data-stu-id="0e5b6-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="0e5b6-105">[Холостудио](https://www.youtube.com/watch?v=BRIJG0x_We8) был одним из первых приложений Майкрософт для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="0e5b6-106">Поэтому нам пришлось создавать новые рекомендации по трехмерному ИНТЕРФЕЙСу и проектированию взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="0e5b6-107">Мы сделали это с помощью многих пользовательских тестов, создания прототипов, проб и ошибок.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="0e5b6-108">Мы понимаем, что ни у кого нет ресурсов на их удаление для проведения исследований, поэтому у нас есть SR. holographic Designer, Маркус Гхали, поделиться тремя вещейми, которые мы узнали во время разработки Холостудио о пользовательском интерфейсе и проектировании взаимодействия для приложений HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="0e5b6-109">Просмотрите видео</span><span class="sxs-lookup"><span data-stu-id="0e5b6-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="0e5b6-110">#1 проблемы: Люди не хотят перемещаться вокруг их создания</span><span class="sxs-lookup"><span data-stu-id="0e5b6-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="0e5b6-111">Мы изначально разработали Workbench в Холостудио в виде прямоугольника, как в реальной жизни.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="0e5b6-112">Проблема заключается в том, что у пользователей есть время существования, которое говорит, что они остаются в рабочем месте или работают перед компьютером, так что они не переходили по Workbench и изучены их трехмерное создание со всех сторон.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![Прямоугольное проектирование Workbench в Холостудио диссуадед пользователей от перемещения и просмотра их создания со всех сторон.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="0e5b6-114">Мы имели представление о том, что требуется округлить Workbench, чтобы не существовало «Front» или «неясного» места.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="0e5b6-115">Когда мы проверили это, внезапно люди начали перемещаться и изучать свои собственные решения.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![Циклическая конструкция Workbench позволяет пользователям пройти весь процесс создания.](images/circular-workbench-500px.jpg)

<span data-ttu-id="0e5b6-117">**Полученные сведения**</span><span class="sxs-lookup"><span data-stu-id="0e5b6-117">**What we learned**</span></span>

<span data-ttu-id="0e5b6-118">Всегда следует думать о том, что удобно для пользователя.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="0e5b6-119">Использование преимуществ своего физического пространства — замечательная функция HoloLens и что-то не так с другими устройствами.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="0e5b6-120">#2 проблемы: Иногда модальные диалоговые окна выходят за рамки holographic</span><span class="sxs-lookup"><span data-stu-id="0e5b6-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="0e5b6-121">Иногда пользователь может найти другое направление от чего-то, что требует внимания в приложении.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="0e5b6-122">На компьютере можно просто открыть диалоговое окно, но если сделать это на любом человеке в трехмерной среде, это может показаться, что диалоговое окно получается по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="0e5b6-123">Они потребуются для чтения сообщения, но их порывом попытаются разоойти.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="0e5b6-124">Эта реакция отлично подходит для игр, но в средстве, предназначенной для работы, она является менее идеальной.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="0e5b6-125">После выполнения нескольких различных задач мы наконец сопоставлены с использованием системы "идейное пузырьковое" для наших диалоговых окон и добавили тендрилс, которые пользователи могут отслеживать, когда в нашем приложении нужно обратить внимание.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="0e5b6-126">Мы также сделали тендрилс пульс, который подразумевает смысл направленности, чтобы пользователи знали, куда идти.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![Система "идейное пузырьковая" включала в себя пулсинг тендрилс, который предоставил представление о направлении, ведущих пользователей и требующих внимания в приложении.](images/thought-bubble-500px.jpg)

<span data-ttu-id="0e5b6-128">**Полученные сведения**</span><span class="sxs-lookup"><span data-stu-id="0e5b6-128">**What we learned**</span></span>

<span data-ttu-id="0e5b6-129">Объем трехмерной графики намного труднее, чтобы предупредить пользователей о том, что им нужно уделять.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="0e5b6-130">Использование менеджеров по контролю внимания, таких как [Пространственный звук](spatial-sound.md), лампочки или пузырьковые пузырьки, может привести к тому, чтобы пользователи могли их там, где это необходимо.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="0e5b6-131">#3 проблемы: Иногда пользовательский интерфейс может блокироваться другими голограммами</span><span class="sxs-lookup"><span data-stu-id="0e5b6-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="0e5b6-132">Бывают случаи, когда пользователь хочет взаимодействовать с голограммой и связанными с ним элементами управления пользовательского интерфейса, но они заблокированы, так как перед ними находится другая голограмма.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="0e5b6-133">Во время разработки Холостудио мы использовали пробную версию и ошибку, чтобы приступить к решению этой проблемы.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Элемент управления пользовательского интерфейса, связанный с голограммой, может быть заблокирован, если между ним и пользователем людьми HoloLens есть другая голограмма.](images/ui-blocked-500px.jpg)

<span data-ttu-id="0e5b6-135">Мы попытались переместить элемент управления ИП ближе к пользователю, чтобы он не мог блокироваться, но не был уверен, что ему не было удобно просматривать элемент управления, который был почти сейчас, одновременно просматривая голограмму.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="0e5b6-136">Однако если элемент управления переместился перед ближайшей голограммой к пользователю, он кажется, что он отсоединился от голограммы, на которую он должен влиять.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="0e5b6-137">Наконец, мы завершили Создание фантомных элементов управления ИП и поместили его на тот же расстоянии от пользователя, что и в голограмме, с которой он связан.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="0e5b6-138">Это позволяет пользователю взаимодействовать с элементом управления, даже если он скрыт.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![Решение. Мы создали элемент управления пользовательского интерфейса, который позволял взаимодействовать с элементом управления и сделал его подсоединенным с голограммой, на которую он влияет.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="0e5b6-140">**Полученные сведения**</span><span class="sxs-lookup"><span data-stu-id="0e5b6-140">**What we learned**</span></span>

<span data-ttu-id="0e5b6-141">Пользователи должны иметь возможность легко получить доступ к элементам управления пользовательского интерфейса, даже если они были заблокированы, чтобы определить, что пользователи могут выполнять свои задачи независимо от того, где их голограммы находятся в реальной жизни.</span><span class="sxs-lookup"><span data-stu-id="0e5b6-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="0e5b6-142">Об авторе</span><span class="sxs-lookup"><span data-stu-id="0e5b6-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="0e5b6-143"><b>Маркус Гхали</b></span><span class="sxs-lookup"><span data-stu-id="0e5b6-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="0e5b6-144">Конструктор SR. holographic@Microsoft</span><span class="sxs-lookup"><span data-stu-id="0e5b6-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="0e5b6-145">См. также</span><span class="sxs-lookup"><span data-stu-id="0e5b6-145">See also</span></span>
* [<span data-ttu-id="0e5b6-146">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="0e5b6-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
