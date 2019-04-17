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
# <a name="implement-3d-app-launchers-uwp-apps"></a>Реализовать средствах запуска трехмерных приложений (приложения UWP)

> [!NOTE]
> Эта функция была добавлена как часть 2017 Fall Creators Update (RS3) для иммерсивную и поддерживается HoloLens с Windows 10 апреля 2018 г. обновление. Убедитесь, что приложение предназначено для версии пакета SDK для Windows больше или равно 10.0.16299 на Иммерсивную и 10.0.17125 на HoloLens. Можно найти последнюю версию пакета Windows SDK [здесь](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

[Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) является отправной точкой, где пользователи будут располагаться перед запуском приложения. При создании приложения универсальной платформы Windows для Windows Mixed Reality, по умолчанию, приложения запускаются как двумерный портативные ПК с эмблемой свое приложение. При разработке взаимодействия для Windows Mixed Reality, 3D запуска можно определять для переопределения 2D по умолчанию средство запуска для вашего приложения. Как правило трехмерной средствах запуска рекомендуются для запуска иммерсивных приложений, которые принимают выход пользователей из Windows Mixed Reality home, тогда как средство запуска 2D по умолчанию является предпочтительным при активации приложения на месте. Вы также можете создать [3D прямая ссылка (secondaryTile)](#3d-deep-links-secondarytiles) как 3D запуска на содержимое в 2D приложения универсальной платформы Windows.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>Процесс создания приложения трехмерной запуска

Существует 3 шага к созданию запуска трехмерных приложений:
1. [Проектирование и concepting](3d-app-launcher-design-guidance.md)
2. [Моделирование и экспорт](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Интеграции его в приложении (Эта статья)

Трехмерных ресурсов, который будет служить средствах запуска для вашего приложения должен быть создан с использованием [Windows Mixed Reality, руководство по созданию](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) для обеспечения совместимости. Ресурсы, которые не соответствуют этой разработки спецификации, не будет отображаться в Windows Mixed Reality home.

## <a name="configuring-the-3d-launcher"></a>Настройка запуска 3D

При создании нового проекта в Visual Studio создается простая стандартная плитка, которая отображает имя и логотип приложения. Чтобы заменить этот 2D представление с пользовательской трехмерной модели изменения приложения с помощью манифеста приложения для включения элемента «MixedRealityModel» как часть определения плитки по умолчанию. Чтобы вернуться к 2D запуска просто удалить определение MixedRealityModel из манифеста.

### <a name="xml"></a>XML

Во-первых найдите манифест пакета приложения в текущем проекте. По умолчанию манифест будет называться Package.appxmanifest. Если вы используете Visual Studio, затем щелкните правой кнопкой мыши манифест в средстве просмотра решений и выберите **Просмотр исходного кода** для открытия xml для редактирования. 

В верхней части манифеста добавьте схему uap5 и включить его в качестве пространством имен можно игнорировать:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Далее следует указываете «MixedRealityModel» на плитке по умолчанию для вашего приложения:

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

Элементы MixedRealityModel принимает путь к файлу, указывающий на трехмерных активов, хранимых в пакете приложения. В настоящее время доставки в формате .glb только трехмерных моделей и к [трехмерного ресурса Windows Mixed Reality разработки инструкции](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) поддерживаются. Ресурсы, которые должны храниться в пакете приложения и анимации в настоящее время не поддерживается. Если параметр «Path» оставлено пустым Windows будет показывать 2D Сланец вместо запуска 3D. **Примечание:** активов .glb должны иметь отметку «Content» в параметрах сборки до построения и запуска приложения.


![Выберите .glb в обозревателе решений и используйте разделе "Свойства", чтобы пометить его как «Содержимое» в параметрах сборки](images/buildsetting-content-300px.png)<br>
*Выберите .glb в обозревателе решений и используйте разделе "Свойства", чтобы пометить его как «Содержимое» в параметрах сборки*

### <a name="bounding-box"></a>Ограничивающий прямоугольник

Позволяет при необходимости добавить область буфера вокруг объекта ограничивающий прямоугольник. Ограничивающий прямоугольник указывается с помощью центральной точки и экстенты, которые указывают расстояние от центра ограничивающего к краям каждой оси. Единицы измерения для ограничивающего прямоугольника можно сопоставить с 1 единицей = 1 метра. Если не указано ограничивающий прямоугольник затем один будет автоматически помещается в сетку объекта. Если предоставленный ограничивающего меньше, чем модели он будет изменен в соответствии с сетки.

Поддержка ограничивающий поле атрибута поступит с обновлением Windows RS4 как свойство элемента MixedRealityModel. Сначала определить ограничивающий прямоугольник в верхней части приложения добавьте схему uap6 манифест и включить их в качестве ignorable пространств имен:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Далее на MixedRealityModel свойству SpatialBoundingBox определение ограничивающего прямоугольника: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>С помощью Unity

При работе с Unity проект должен быть построен и открыт в Visual Studio, прежде чем можно изменить манифест приложения. 

>[!NOTE]
>3D запуска должны быть переопределены в манифесте, при создании и развертывании новое решение Visual Studio из Unity.

## <a name="3d-deep-links-secondarytiles"></a>3D глубокого связывает (secondaryTiles)

> [!NOTE]
> Эта функция была добавлена как часть 2017 Fall Creators Update (RS3) для иммерсивную (VR) и как часть апреля 2018 г. обновление (RS4) для HoloLens. Убедитесь, что приложение предназначено для версии пакета SDK для Windows больше или равно 10.0.16299 на иммерсивную (VR) и 10.0.17125 на HoloLens. Можно найти последнюю версию пакета Windows SDK [здесь](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>3D прямых ссылок (secondaryTiles) работают только с 2D приложений универсальной платформы Windows. Тем не менее, можно создать [запуска трехмерных приложений](implementing-3d-app-launchers.md) для запуска эксклюзивные приложения из Windows Mixed Reality home.

Можно улучшить 2D приложений для Windows Mixed Reality, добавив возможность разместить 3D-моделей из приложения в [Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) как прямые ссылки на содержимое в приложении 2D так же, как [2D получателя плитки](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) меню Пуск в Windows. Например можно создать photospheres 360°, связь непосредственно в приложение 360° photo viewer, или пользователи могут поместить трехмерного содержимого из коллекции ресурсов, которая открывает страницу сведений об авторе. Это только некоторые способы для расширения функциональности приложения на 2D в 3D-содержимого.

### <a name="creating-a-3d-secondarytile"></a>Создание трехмерной «secondaryTile»

Можно поместить трехмерного содержимого из приложения с помощью «secondaryTiles» путем определения модели смешанной реальности во время создания. Смешанная реальность модели создаются, ссылаясь на трехмерного ресурса в пакете приложения и при необходимости определения ограничивающий прямоугольник. 

> [!NOTE]
> Создание «secondaryTiles» из в это монопольное представление в настоящее время не поддерживается.

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

### <a name="bounding-box"></a>Ограничивающий прямоугольник

Чтобы добавить область буфера вокруг объекта ограничивающий прямоугольник можно использовать. Ограничивающий прямоугольник указывается с помощью центральной точки и экстенты, которые указывают расстояние от центра ограничивающего к краям каждой оси. Единицы измерения для ограничивающего прямоугольника можно сопоставить с 1 единицей = 1 метра. Если не указано ограничивающий прямоугольник затем один будет автоматически помещается в сетку объекта. Если предоставленный ограничивающего меньше, чем модели он будет изменен в соответствии с сетки.

### <a name="activation-behavior"></a>Поведение активации

> [!NOTE]
> Эта функция будет поддерживаться на момент изменения Windows RS4. Убедитесь, что приложение предназначено на версию пакета SDK Windows, не меньше 10.0.17125, если вы планируете использовать эту функцию

Можно определить поведение активации для трехмерной secondaryTile для управления, как он будет реагировать при его выборе. Это можно использовать для размещения трехмерных объектов в смешанной реальности Домашняя, которые purley информативные или фигурную. Поддерживаются следующие типы поведения активации:
1. Default: Когда пользователь выбирает 3D secondaryTile активации приложения
2. NONE: При выборе 3D secondaryTile, ничего не происходит и приложение не активировано.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Получение и обновление существующих «secondaryTile»

Разработчикам можно вернуть список их существующие вспомогательные плитки, включая свойства, которые они уже указали. Они также могут обновлять свойства путем изменения значения и последующего вызова UpdateAsync().

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Проверка того, что пользователь находится в Windows Mixed Reality

3D прямых ссылок (secondaryTiles) может создаваться только в тех случаях, когда представление отображается в гарнитуры смешанной реальности Windows. При представлении не представляемых гарнитуры смешанной реальности Windows рекомендуется аккуратная обработка это путем сокрытия точку входа, либо отображается сообщение об ошибке. Это можно проверить, запросив [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Уведомления на плитках

Уведомлений на плитке в настоящее время не поддерживают отправку обновленных данных с помощью трехмерных активов. Это означает, что разработчики нельзя будет сделать следующее
* Push-уведомлений
* Периодический опрос
* Запланированных уведомлений

Дополнительные сведения о другой плитки функций и атрибутов и их использовании для 2D плиток ссылаются на [плитки для приложений универсальной платформы Windows документации](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>См. также

* [Образец модели смешанной реальности](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) содержащий запуска трехмерных приложений.
* [Руководство по проектированию приложения трехмерной запуска](3d-app-launcher-design-guidance.md)
* [Создании трехмерных моделей для использования в домашних Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Реализация средствах запуска трехмерных приложений (приложения Win32)](implementing-3d-app-launchers-win32.md)
* [Перемещение Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)
