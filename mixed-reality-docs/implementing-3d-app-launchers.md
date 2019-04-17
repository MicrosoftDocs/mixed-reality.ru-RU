---
title: Реализовать средствах запуска трехмерных приложений (приложения UWP)
description: Как создать средствах запуска приложений 3D и логотипы для смешанной реальности UWP Windows-приложений и игр, (распространяться через Microsoft Store), и на HoloLens и иммерсивную (VR).
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, логотип, значок, моделирования, средства запуска, 3D запуска, плитки, динамической куба, прямая ссылка, secondarytile, вторичная плитка, универсальной платформы Windows
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604856"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="2ca27-104">Реализовать средствах запуска трехмерных приложений (приложения UWP)</span><span class="sxs-lookup"><span data-stu-id="2ca27-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="2ca27-105">Эта функция была добавлена как часть 2017 Fall Creators Update (RS3) для иммерсивную и поддерживается HoloLens с Windows 10 апреля 2018 г. обновление.</span><span class="sxs-lookup"><span data-stu-id="2ca27-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="2ca27-106">Убедитесь, что приложение предназначено для версии пакета SDK для Windows больше или равно 10.0.16299 на Иммерсивную и 10.0.17125 на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ca27-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="2ca27-107">Можно найти последнюю версию пакета Windows SDK [здесь](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="2ca27-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="2ca27-108">[Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) является отправной точкой, где пользователи будут располагаться перед запуском приложения.</span><span class="sxs-lookup"><span data-stu-id="2ca27-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="2ca27-109">При создании приложения универсальной платформы Windows для Windows Mixed Reality, по умолчанию, приложения запускаются как двумерный портативные ПК с эмблемой свое приложение.</span><span class="sxs-lookup"><span data-stu-id="2ca27-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="2ca27-110">При разработке взаимодействия для Windows Mixed Reality, 3D запуска можно определять для переопределения 2D по умолчанию средство запуска для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="2ca27-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="2ca27-111">Как правило трехмерной средствах запуска рекомендуются для запуска иммерсивных приложений, которые принимают выход пользователей из Windows Mixed Reality home, тогда как средство запуска 2D по умолчанию является предпочтительным при активации приложения на месте.</span><span class="sxs-lookup"><span data-stu-id="2ca27-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="2ca27-112">Вы также можете создать [3D прямая ссылка (secondaryTile)](#3d-deep-links-secondarytiles) как 3D запуска на содержимое в 2D приложения универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="2ca27-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="2ca27-113">Процесс создания приложения трехмерной запуска</span><span class="sxs-lookup"><span data-stu-id="2ca27-113">3D app launcher creation process</span></span>

<span data-ttu-id="2ca27-114">Существует 3 шага к созданию запуска трехмерных приложений:</span><span class="sxs-lookup"><span data-stu-id="2ca27-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="2ca27-115">Проектирование и concepting</span><span class="sxs-lookup"><span data-stu-id="2ca27-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="2ca27-116">Моделирование и экспорт</span><span class="sxs-lookup"><span data-stu-id="2ca27-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="2ca27-117">Интеграции его в приложении (Эта статья)</span><span class="sxs-lookup"><span data-stu-id="2ca27-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="2ca27-118">Трехмерных ресурсов, который будет служить средствах запуска для вашего приложения должен быть создан с использованием [Windows Mixed Reality, руководство по созданию](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) для обеспечения совместимости.</span><span class="sxs-lookup"><span data-stu-id="2ca27-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="2ca27-119">Ресурсы, которые не соответствуют этой разработки спецификации, не будет отображаться в Windows Mixed Reality home.</span><span class="sxs-lookup"><span data-stu-id="2ca27-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="2ca27-120">Настройка запуска 3D</span><span class="sxs-lookup"><span data-stu-id="2ca27-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="2ca27-121">При создании нового проекта в Visual Studio создается простая стандартная плитка, которая отображает имя и логотип приложения.</span><span class="sxs-lookup"><span data-stu-id="2ca27-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="2ca27-122">Чтобы заменить этот 2D представление с пользовательской трехмерной модели изменения приложения с помощью манифеста приложения для включения элемента «MixedRealityModel» как часть определения плитки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2ca27-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="2ca27-123">Чтобы вернуться к 2D запуска просто удалить определение MixedRealityModel из манифеста.</span><span class="sxs-lookup"><span data-stu-id="2ca27-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="2ca27-124">XML</span><span class="sxs-lookup"><span data-stu-id="2ca27-124">XML</span></span>

<span data-ttu-id="2ca27-125">Во-первых найдите манифест пакета приложения в текущем проекте.</span><span class="sxs-lookup"><span data-stu-id="2ca27-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="2ca27-126">По умолчанию манифест будет называться Package.appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="2ca27-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="2ca27-127">Если вы используете Visual Studio, затем щелкните правой кнопкой мыши манифест в средстве просмотра решений и выберите **Просмотр исходного кода** для открытия xml для редактирования.</span><span class="sxs-lookup"><span data-stu-id="2ca27-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="2ca27-128">В верхней части манифеста добавьте схему uap5 и включить его в качестве пространством имен можно игнорировать:</span><span class="sxs-lookup"><span data-stu-id="2ca27-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="2ca27-129">Далее следует указываете «MixedRealityModel» на плитке по умолчанию для вашего приложения:</span><span class="sxs-lookup"><span data-stu-id="2ca27-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="2ca27-130">Элементы MixedRealityModel принимает путь к файлу, указывающий на трехмерных активов, хранимых в пакете приложения.</span><span class="sxs-lookup"><span data-stu-id="2ca27-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="2ca27-131">В настоящее время доставки в формате .glb только трехмерных моделей и к [трехмерного ресурса Windows Mixed Reality разработки инструкции](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="2ca27-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="2ca27-132">Ресурсы, которые должны храниться в пакете приложения и анимации в настоящее время не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="2ca27-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="2ca27-133">Если параметр «Path» оставлено пустым Windows будет показывать 2D Сланец вместо запуска 3D.</span><span class="sxs-lookup"><span data-stu-id="2ca27-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="2ca27-134">**Примечание:** активов .glb должны иметь отметку «Content» в параметрах сборки до построения и запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="2ca27-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="2ca27-135">![Выберите .glb в обозревателе решений и используйте разделе "Свойства", чтобы пометить его как «Содержимое» в параметрах сборки](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="2ca27-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="2ca27-136">*Выберите .glb в обозревателе решений и используйте разделе "Свойства", чтобы пометить его как «Содержимое» в параметрах сборки*</span><span class="sxs-lookup"><span data-stu-id="2ca27-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="2ca27-137">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="2ca27-137">Bounding box</span></span>

<span data-ttu-id="2ca27-138">Позволяет при необходимости добавить область буфера вокруг объекта ограничивающий прямоугольник.</span><span class="sxs-lookup"><span data-stu-id="2ca27-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="2ca27-139">Ограничивающий прямоугольник указывается с помощью центральной точки и экстенты, которые указывают расстояние от центра ограничивающего к краям каждой оси.</span><span class="sxs-lookup"><span data-stu-id="2ca27-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="2ca27-140">Единицы измерения для ограничивающего прямоугольника можно сопоставить с 1 единицей = 1 метра.</span><span class="sxs-lookup"><span data-stu-id="2ca27-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="2ca27-141">Если не указано ограничивающий прямоугольник затем один будет автоматически помещается в сетку объекта.</span><span class="sxs-lookup"><span data-stu-id="2ca27-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="2ca27-142">Если предоставленный ограничивающего меньше, чем модели он будет изменен в соответствии с сетки.</span><span class="sxs-lookup"><span data-stu-id="2ca27-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="2ca27-143">Поддержка ограничивающий поле атрибута поступит с обновлением Windows RS4 как свойство элемента MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="2ca27-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="2ca27-144">Сначала определить ограничивающий прямоугольник в верхней части приложения добавьте схему uap6 манифест и включить их в качестве ignorable пространств имен:</span><span class="sxs-lookup"><span data-stu-id="2ca27-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="2ca27-145">Далее на MixedRealityModel свойству SpatialBoundingBox определение ограничивающего прямоугольника:</span><span class="sxs-lookup"><span data-stu-id="2ca27-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="2ca27-146">С помощью Unity</span><span class="sxs-lookup"><span data-stu-id="2ca27-146">Using Unity</span></span>

<span data-ttu-id="2ca27-147">При работе с Unity проект должен быть построен и открыт в Visual Studio, прежде чем можно изменить манифест приложения.</span><span class="sxs-lookup"><span data-stu-id="2ca27-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="2ca27-148">3D запуска должны быть переопределены в манифесте, при создании и развертывании новое решение Visual Studio из Unity.</span><span class="sxs-lookup"><span data-stu-id="2ca27-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="2ca27-149">3D глубокого связывает (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="2ca27-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="2ca27-150">Эта функция была добавлена как часть 2017 Fall Creators Update (RS3) для иммерсивную (VR) и как часть апреля 2018 г. обновление (RS4) для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ca27-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="2ca27-151">Убедитесь, что приложение предназначено для версии пакета SDK для Windows больше или равно 10.0.16299 на иммерсивную (VR) и 10.0.17125 на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ca27-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="2ca27-152">Можно найти последнюю версию пакета Windows SDK [здесь](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="2ca27-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="2ca27-153">3D прямых ссылок (secondaryTiles) работают только с 2D приложений универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="2ca27-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="2ca27-154">Тем не менее, можно создать [запуска трехмерных приложений](implementing-3d-app-launchers.md) для запуска эксклюзивные приложения из Windows Mixed Reality home.</span><span class="sxs-lookup"><span data-stu-id="2ca27-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="2ca27-155">Можно улучшить 2D приложений для Windows Mixed Reality, добавив возможность разместить 3D-моделей из приложения в [Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) как прямые ссылки на содержимое в приложении 2D так же, как [2D получателя плитки](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) меню Пуск в Windows.</span><span class="sxs-lookup"><span data-stu-id="2ca27-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="2ca27-156">Например можно создать photospheres 360°, связь непосредственно в приложение 360° photo viewer, или пользователи могут поместить трехмерного содержимого из коллекции ресурсов, которая открывает страницу сведений об авторе.</span><span class="sxs-lookup"><span data-stu-id="2ca27-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="2ca27-157">Это только некоторые способы для расширения функциональности приложения на 2D в 3D-содержимого.</span><span class="sxs-lookup"><span data-stu-id="2ca27-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="2ca27-158">Создание трехмерной «secondaryTile»</span><span class="sxs-lookup"><span data-stu-id="2ca27-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="2ca27-159">Можно поместить трехмерного содержимого из приложения с помощью «secondaryTiles» путем определения модели смешанной реальности во время создания.</span><span class="sxs-lookup"><span data-stu-id="2ca27-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="2ca27-160">Смешанная реальность модели создаются, ссылаясь на трехмерного ресурса в пакете приложения и при необходимости определения ограничивающий прямоугольник.</span><span class="sxs-lookup"><span data-stu-id="2ca27-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="2ca27-161">Создание «secondaryTiles» из в это монопольное представление в настоящее время не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="2ca27-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="2ca27-162">Ограничивающий прямоугольник</span><span class="sxs-lookup"><span data-stu-id="2ca27-162">Bounding box</span></span>

<span data-ttu-id="2ca27-163">Чтобы добавить область буфера вокруг объекта ограничивающий прямоугольник можно использовать.</span><span class="sxs-lookup"><span data-stu-id="2ca27-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="2ca27-164">Ограничивающий прямоугольник указывается с помощью центральной точки и экстенты, которые указывают расстояние от центра ограничивающего к краям каждой оси.</span><span class="sxs-lookup"><span data-stu-id="2ca27-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="2ca27-165">Единицы измерения для ограничивающего прямоугольника можно сопоставить с 1 единицей = 1 метра.</span><span class="sxs-lookup"><span data-stu-id="2ca27-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="2ca27-166">Если не указано ограничивающий прямоугольник затем один будет автоматически помещается в сетку объекта.</span><span class="sxs-lookup"><span data-stu-id="2ca27-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="2ca27-167">Если предоставленный ограничивающего меньше, чем модели он будет изменен в соответствии с сетки.</span><span class="sxs-lookup"><span data-stu-id="2ca27-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="2ca27-168">Поведение активации</span><span class="sxs-lookup"><span data-stu-id="2ca27-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="2ca27-169">Эта функция будет поддерживаться на момент изменения Windows RS4.</span><span class="sxs-lookup"><span data-stu-id="2ca27-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="2ca27-170">Убедитесь, что приложение предназначено на версию пакета SDK Windows, не меньше 10.0.17125, если вы планируете использовать эту функцию</span><span class="sxs-lookup"><span data-stu-id="2ca27-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="2ca27-171">Можно определить поведение активации для трехмерной secondaryTile для управления, как он будет реагировать при его выборе.</span><span class="sxs-lookup"><span data-stu-id="2ca27-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="2ca27-172">Это можно использовать для размещения трехмерных объектов в смешанной реальности Домашняя, которые purley информативные или фигурную.</span><span class="sxs-lookup"><span data-stu-id="2ca27-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="2ca27-173">Поддерживаются следующие типы поведения активации:</span><span class="sxs-lookup"><span data-stu-id="2ca27-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="2ca27-174">Default: Когда пользователь выбирает 3D secondaryTile активации приложения</span><span class="sxs-lookup"><span data-stu-id="2ca27-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="2ca27-175">NONE: При выборе 3D secondaryTile, ничего не происходит и приложение не активировано.</span><span class="sxs-lookup"><span data-stu-id="2ca27-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="2ca27-176">Получение и обновление существующих «secondaryTile»</span><span class="sxs-lookup"><span data-stu-id="2ca27-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="2ca27-177">Разработчикам можно вернуть список их существующие вспомогательные плитки, включая свойства, которые они уже указали.</span><span class="sxs-lookup"><span data-stu-id="2ca27-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="2ca27-178">Они также могут обновлять свойства путем изменения значения и последующего вызова UpdateAsync().</span><span class="sxs-lookup"><span data-stu-id="2ca27-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="2ca27-179">Проверка того, что пользователь находится в Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2ca27-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="2ca27-180">3D прямых ссылок (secondaryTiles) может создаваться только в тех случаях, когда представление отображается в гарнитуры смешанной реальности Windows.</span><span class="sxs-lookup"><span data-stu-id="2ca27-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="2ca27-181">При представлении не представляемых гарнитуры смешанной реальности Windows рекомендуется аккуратная обработка это путем сокрытия точку входа, либо отображается сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="2ca27-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="2ca27-182">Это можно проверить, запросив [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="2ca27-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="2ca27-183">Уведомления на плитках</span><span class="sxs-lookup"><span data-stu-id="2ca27-183">Tile notifications</span></span>

<span data-ttu-id="2ca27-184">Уведомлений на плитке в настоящее время не поддерживают отправку обновленных данных с помощью трехмерных активов.</span><span class="sxs-lookup"><span data-stu-id="2ca27-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="2ca27-185">Это означает, что разработчики нельзя будет сделать следующее</span><span class="sxs-lookup"><span data-stu-id="2ca27-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="2ca27-186">Push-уведомлений</span><span class="sxs-lookup"><span data-stu-id="2ca27-186">Push Notifications</span></span>
* <span data-ttu-id="2ca27-187">Периодический опрос</span><span class="sxs-lookup"><span data-stu-id="2ca27-187">Periodic Polling</span></span>
* <span data-ttu-id="2ca27-188">Запланированных уведомлений</span><span class="sxs-lookup"><span data-stu-id="2ca27-188">Scheduled Notifications</span></span>

<span data-ttu-id="2ca27-189">Дополнительные сведения о другой плитки функций и атрибутов и их использовании для 2D плиток ссылаются на [плитки для приложений универсальной платформы Windows документации](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="2ca27-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ca27-190">См. также</span><span class="sxs-lookup"><span data-stu-id="2ca27-190">See also</span></span>

* <span data-ttu-id="2ca27-191">[Образец модели смешанной реальности](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) содержащий запуска трехмерных приложений.</span><span class="sxs-lookup"><span data-stu-id="2ca27-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="2ca27-192">Руководство по проектированию приложения трехмерной запуска</span><span class="sxs-lookup"><span data-stu-id="2ca27-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="2ca27-193">Создании трехмерных моделей для использования в домашних Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2ca27-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="2ca27-194">Реализация средствах запуска трехмерных приложений (приложения Win32)</span><span class="sxs-lookup"><span data-stu-id="2ca27-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="2ca27-195">Перемещение Windows Mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="2ca27-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
