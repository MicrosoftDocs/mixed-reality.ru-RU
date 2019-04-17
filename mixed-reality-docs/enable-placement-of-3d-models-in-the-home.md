---
title: Включить размещение трехмерной модели дома
description: Как разместить трехмерные модели из веб-сайта или приложения в Windows Mixed Reality home
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, модели, место на домашней странице, место, всему миру, моделирования, смешанной реальности домашней, Интернет, приложения
ms.openlocfilehash: 3a50353aae8e03c3ebb3ee9ec2f642f21836e925
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605023"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="db476-104">Включение размещения 3D-моделей в смешанной реальности home</span><span class="sxs-lookup"><span data-stu-id="db476-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="db476-105">Эта функция была добавлена как часть [обновления Windows 10 апреля 2018 г.](release-notes-april-2018.md).</span><span class="sxs-lookup"><span data-stu-id="db476-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md).</span></span> <span data-ttu-id="db476-106">Более старые версии Windows не совместимы с помощью этой функции.</span><span class="sxs-lookup"><span data-stu-id="db476-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="db476-107">[Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) является отправной точкой, где пользователи будут располагаться перед запуском приложения.</span><span class="sxs-lookup"><span data-stu-id="db476-107">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="db476-108">В некоторых сценариях 2D приложения (такие как голограммы) целенаправленного размещения трехмерных моделей непосредственно в домашней смешанной реальности, как оформление или для дальнейшей проверки в полностью трехмерном режиме.</span><span class="sxs-lookup"><span data-stu-id="db476-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="db476-109">*Добавьте протокол модели* можно отправить к трехмерной модели из веб-сайта или приложения непосредственно в Windows Mixed Reality дома, где будет сохраняться, например [средствах запуска приложений 3D](3d-app-launcher-design-guidance.md), 2D приложения и голограммы.</span><span class="sxs-lookup"><span data-stu-id="db476-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="db476-110">Например, если вы разрабатываете приложения который предоставляет доступ к a каталога 3D мебели по проектированию пробел, можно использовать *добавьте протокол модели* позволяет поместить этих моделей 3D мебель из каталога.</span><span class="sxs-lookup"><span data-stu-id="db476-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, you can use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="db476-111">После размещения в мире пользователей можно перемещать, масштабировать и удалить эти трехмерных моделей, так же, как другие голограммы домашних.</span><span class="sxs-lookup"><span data-stu-id="db476-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="db476-112">В этой статье представлен обзор реализации *добавьте протокол модели* , что можно запускать разрешение пользователям снабдить их мир с трехмерными объектами из приложения или в Интернете.</span><span class="sxs-lookup"><span data-stu-id="db476-112">This article provides an overview of implementing the *add model protocol* so that you can start enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="db476-113">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="db476-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="db476-114">Компонент</span><span class="sxs-lookup"><span data-stu-id="db476-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="db476-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="db476-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="db476-116"><a href="immersive-headset-hardware-details.md">Иммерсивную</a></span><span class="sxs-lookup"><span data-stu-id="db476-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="db476-117">Добавление протокола модели</span><span class="sxs-lookup"><span data-stu-id="db476-117">Add model protocol</span></span></td><td style="text-align: center;"> <span data-ttu-id="db476-118">✔️</span><span class="sxs-lookup"><span data-stu-id="db476-118">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="db476-119">✔️</span><span class="sxs-lookup"><span data-stu-id="db476-119">✔️</span></span></td>
</tr>
</table>

## <a name="overview"></a><span data-ttu-id="db476-120">Обзор</span><span class="sxs-lookup"><span data-stu-id="db476-120">Overview</span></span>

<span data-ttu-id="db476-121">Разрешить размещение трехмерными моделями в Windows Mixed Reality домашней пользователю 2 этапов.</span><span class="sxs-lookup"><span data-stu-id="db476-121">There are 2 steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="db476-122">[Обеспечить совместимость с Windows Mixed Reality домашней 3D-модели](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="db476-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="db476-123">Реализуйте *добавьте протокол модели* в ваше приложение или веб-страницу (в этой статье).</span><span class="sxs-lookup"><span data-stu-id="db476-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="db476-124">Реализация *добавьте протокол модели*</span><span class="sxs-lookup"><span data-stu-id="db476-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="db476-125">При наличии [совместимых трехмерной модели](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), можно реализовать *добавьте протокол модели* , активировав следующий URI из любой веб-страницы или приложения:</span><span class="sxs-lookup"><span data-stu-id="db476-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="db476-126">Если URI указывает на удаленном ресурсе, затем он будет автоматически быть загружается и помещается в доме.</span><span class="sxs-lookup"><span data-stu-id="db476-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="db476-127">Локальные ресурсы будут скопированы в папку данных приложения смешанной реальности Домашняя до помещения в доме.</span><span class="sxs-lookup"><span data-stu-id="db476-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="db476-128">Мы рекомендуем проектирование вашей работой учетной записи для сценариев, где пользователь может работать под управлением более ранней версии Windows, который не поддерживает эту функцию, скрыв кнопки или отключить его, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="db476-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="db476-129">Вызов *добавьте протокол модели* из приложения универсальной платформы Windows:</span><span class="sxs-lookup"><span data-stu-id="db476-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="db476-130">Вызов *добавьте протокол модели* на веб-странице:</span><span class="sxs-lookup"><span data-stu-id="db476-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="db476-131">Рекомендации по иммерсивную (VR)</span><span class="sxs-lookup"><span data-stu-id="db476-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="db476-132">Для иммерсивную (VR) портале смешанной реальности не должны быть запущены перед вызовом *добавьте протокол модели*.</span><span class="sxs-lookup"><span data-stu-id="db476-132">For immersive (VR) headsets, the Mixed Reality Portal does not have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="db476-133">В этом случае *добавьте протокол модели* запустится портале смешанной реальности и поместить объект непосредственно где гарнитура смотрит после появления в смешанной реальности home.</span><span class="sxs-lookup"><span data-stu-id="db476-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="db476-134">При вызове *добавьте протокол модели* с рабочего стола с помощью смешанной реальности портала уже выполняется, убедитесь, что гарнитура «переходит в спящий режим».</span><span class="sxs-lookup"><span data-stu-id="db476-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="db476-135">В противном случае размещение не удастся.</span><span class="sxs-lookup"><span data-stu-id="db476-135">If not, the placement will not succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="db476-136">См. также</span><span class="sxs-lookup"><span data-stu-id="db476-136">See also</span></span>

* [<span data-ttu-id="db476-137">Создании трехмерных моделей для использования в домашних Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="db476-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="db476-138">Перемещение Windows Mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="db476-138">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
