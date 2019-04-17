---
title: Пример использования - 3 HoloStudio пользовательский Интерфейс и взаимодействие разработки полученные данные для
description: Пользовательский Интерфейс HoloStudio и полученные данные разработки для взаимодействия
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: Windows HoloLens, HoloStudio, смешанной реальности
ms.openlocfilehash: 217c489fed3c0588dae1c2753db6ba15da3522c8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603208"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="d1803-104">Пример использования - 3 HoloStudio пользовательский Интерфейс и взаимодействие разработки полученные данные для</span><span class="sxs-lookup"><span data-stu-id="d1803-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="d1803-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) был одним из первого приложения Майкрософт для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d1803-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="d1803-106">По этой причине нам пришлось создавать новые рекомендации для 3D пользовательского интерфейса и разработка взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="d1803-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="d1803-107">Мы сделали это пройти через немало пользовательского тестирования, создания прототипов и проб и ошибок.</span><span class="sxs-lookup"><span data-stu-id="d1803-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="d1803-108">Мы знаем, что не у всех есть ресурсы в их распоряжении, для выполнения такого рода исследований, поэтому у нас было нашей старший Holographic конструкторе Ghaly Маркус совместно использовать три вещи мы узнали во время разработки HoloStudio о разработке пользовательского интерфейса и взаимодействие для HoloLens приложений.</span><span class="sxs-lookup"><span data-stu-id="d1803-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="d1803-109">Просмотрите видео</span><span class="sxs-lookup"><span data-stu-id="d1803-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="d1803-110">Проблема #1. Пользователям не нужно перемещать их создание</span><span class="sxs-lookup"><span data-stu-id="d1803-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="d1803-111">Мы изначально разработаны workbench в HoloStudio как прямоугольник, во многом как можно найти в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="d1803-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="d1803-112">Проблема в том, что пользователи имеют срок существования качества, уведомляющее о оставаться по-прежнему в том случае, когда они сидят за столом или работа перед компьютера, поэтому они не были перемещения workbench и изучение их 3D-разработки из всех сторон.</span><span class="sxs-lookup"><span data-stu-id="d1803-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![Прямоугольная структура workbench в HoloStudio dissuaded пользователям перемещения и просматривать свои творения из всех сторон.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="d1803-114">У нас было помогает в принятии workbench округления, таким образом, чтобы было не «front» или снимите месте, которое вы предполагалось, что готовы.</span><span class="sxs-lookup"><span data-stu-id="d1803-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="d1803-115">Когда мы проверили этот способ, внезапно людей перемещения и начать изучение их творения сами по себе.</span><span class="sxs-lookup"><span data-stu-id="d1803-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![Циклическая workbench разработки рекомендуется пользователей вплоть присутствия за их создание.](images/circular-workbench-500px.jpg)

<span data-ttu-id="d1803-117">**Чему мы научились**</span><span class="sxs-lookup"><span data-stu-id="d1803-117">**What we learned**</span></span>

<span data-ttu-id="d1803-118">Всегда думайте о том, что неудобно для пользователя.</span><span class="sxs-lookup"><span data-stu-id="d1803-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="d1803-119">Преимущества от их физического пространства является замечательную функцию HoloLens и то, что невозможно в случае с другими устройствами.</span><span class="sxs-lookup"><span data-stu-id="d1803-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="d1803-120">Проблема #2. Модальные диалоговые окна иногда выходят за рамки holographic</span><span class="sxs-lookup"><span data-stu-id="d1803-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="d1803-121">В некоторых случаях пользователь может выглядеть используется другой подход, что-то из, требующим внимания в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="d1803-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="d1803-122">На ПК можно просто всплывающее окно вверх диалоговое окно, но после этого в чьей лиц в среде 3D, она чувствуют себя словно диалогового окна является получение в свой путь.</span><span class="sxs-lookup"><span data-stu-id="d1803-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="d1803-123">Необходимо, чтобы прочитать сообщение, но их порывом является установка для получения исходящими.</span><span class="sxs-lookup"><span data-stu-id="d1803-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="d1803-124">Такой реакции отлично, если вы воспроизводите игру, но в это средство, предназначенное для работы, это не идеальное положение вещей.</span><span class="sxs-lookup"><span data-stu-id="d1803-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="d1803-125">После ознакомления со службами несколько других функций, мы наконец остановился на с помощью системы «рассматривать пузырек» для наших диалоговых окон и добавили tendrils, которые могут использоваться для которых требуется их внимания в нашем приложении.</span><span class="sxs-lookup"><span data-stu-id="d1803-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="d1803-126">Мы также внесли pulse tendrils, который содержится в разрешении чувства направленность таким образом, чтобы пользователи знали, где можно найти.</span><span class="sxs-lookup"><span data-stu-id="d1803-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![Система «Рассматривать сфере» включены пульсирующий tendrils, которые предоставлены представление о направлении, приводит к необходимости их внимания в приложении пользователи.](images/thought-bubble-500px.jpg)

<span data-ttu-id="d1803-128">**Чему мы научились**</span><span class="sxs-lookup"><span data-stu-id="d1803-128">**What we learned**</span></span>

<span data-ttu-id="d1803-129">Это гораздо сложнее в трехмерном пространстве, чтобы оповестить пользователей к вещам, они должны обращать внимание на.</span><span class="sxs-lookup"><span data-stu-id="d1803-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="d1803-130">С помощью директоров внимания, например [пространственных звук](spatial-sound.md), светло-лучи или восходящую маршрутизацию мысль, может привести к которой они должны быть пользователей.</span><span class="sxs-lookup"><span data-stu-id="d1803-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="d1803-131">Проблема #3. Иногда пользовательский Интерфейс может быть заблокирован другим голограммы</span><span class="sxs-lookup"><span data-stu-id="d1803-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="d1803-132">Бывают случаи, когда пользователю необходимо взаимодействовать с голограмма и его связанные элементы управления пользовательского интерфейса, но они заблокированы из представления, так как другой голограмма перед их.</span><span class="sxs-lookup"><span data-stu-id="d1803-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="d1803-133">Хотя мы разрабатывали HoloStudio, приходят к решению для этого мы использовали проб и ошибок.</span><span class="sxs-lookup"><span data-stu-id="d1803-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Элемент управления пользовательского интерфейса, связанный с голограмма могут быть заблокированы, если имеется другой голограмма между ним и пользователя, то HoloLens.](images/ui-blocked-500px.jpg)

<span data-ttu-id="d1803-135">Мы пытались перемещение ближе к элемента управления пользовательского интерфейса для пользователя, поэтому его не удалось получить блокируется, но и найти, что он не решилась для пользователя представить себе элемент управления, который был рядом вы просматривая одновременно голограмма, которая была слишком далеко от.</span><span class="sxs-lookup"><span data-stu-id="d1803-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="d1803-136">Если, однако мы перемещен элемент перед ближайшим голограмма пользователю, они посчитали, как она была отсоединена от голограмма, которые должны влиять.</span><span class="sxs-lookup"><span data-stu-id="d1803-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="d1803-137">Мы наконец завершения установки элемента управления пользовательского интерфейса и поместить его на одинаковом расстоянии от пользователя как голограмма, связанными с, поэтому оба они будут чувствовать себя подключенной.</span><span class="sxs-lookup"><span data-stu-id="d1803-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="d1803-138">Это позволяет пользователю взаимодействовать с элементом управления, несмотря на то, что он закрывается.</span><span class="sxs-lookup"><span data-stu-id="d1803-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![Решение: мы синхронизирован. элемент управления пользовательского интерфейса, который разрешен взаимодействия с элементом управления и внесенные будет восприниматься подключен к голограмма, она влияет на.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="d1803-140">**Чему мы научились**</span><span class="sxs-lookup"><span data-stu-id="d1803-140">**What we learned**</span></span>

<span data-ttu-id="d1803-141">Пользователи должны иметь возможность легко обращаться к элементов управления пользовательского интерфейса, даже если они были заблокированы, поэтому подумайте методов, чтобы гарантировать, что пользователям выполнить свои задачи, независимо от того, где находятся их голограммы в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="d1803-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="d1803-142">Об авторе</span><span class="sxs-lookup"><span data-stu-id="d1803-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d1803-143"><b>Маркус Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="d1803-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="d1803-144">Старший конструктор Holographic @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d1803-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="d1803-145">См. также</span><span class="sxs-lookup"><span data-stu-id="d1803-145">See also</span></span>
* [<span data-ttu-id="d1803-146">Основы взаимодействия</span><span class="sxs-lookup"><span data-stu-id="d1803-146">Interaction fundamentals</span></span>](interaction-fundamentals.md)

 
