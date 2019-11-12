---
title: Реализация запуска 3D-приложений (приложения UWP)
description: Как создать трехмерные программы запуска и логотипы для приложений и игр Windows Mixed Reality (распространяется через Microsoft Store) как на HoloLens, так и в иммерсивного (VR) гарнитурах.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Эмблема, значок, моделирование, средство запуска, трехмерное средство запуска, плитка, динамический куб, глубокая ссылка, секондаритиле, вспомогательная плитка, UWP
ms.openlocfilehash: 5d18f699792760c39df4f814bde470fb9f889db7
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926771"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Реализация запуска 3D-приложений (приложения UWP)

> [!NOTE]
> Эта функция была добавлена как часть обновления 2017 в RS3 (Creator) для впечатляющих головных телефонов и поддерживается в HoloLens с обновлением Windows 10 от апреля 2018. Убедитесь, что приложение предназначено для версии Windows SDK больше или равно 10.0.16299 на впечатляющих гарнитурах и 10.0.17125 в HoloLens. Последнюю Windows SDK можно найти [здесь](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

[Главная страница Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) — это отправная точка, в которой пользователи начинают работу перед запуском приложений. При создании приложения UWP для Windows Mixed Reality приложения по умолчанию запускаются в виде двумерных планшетов с логотипом своего приложения. При разработке функций для Windows Mixed Reality при необходимости можно определить трехмерное средство запуска для переопределения 2D-запуска по умолчанию для приложения. В общем случае трехмерные запуски рекомендуются для запуска впечатляющих приложений, которые принимают пользователей из дома Windows Mixed Reality, в то время как по умолчанию используется 2D-средство запуска, когда приложение активируется на месте. Можно также создать [трехмерную глубину ссылки (секондаритиле)](#3d-deep-links-secondarytiles) в виде трехмерного модуля запуска для содержимого в ДВУХМЕРНОМ приложении UWP.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>процесс создания средства запуска приложений 3D

Создание средства запуска 3D-приложений состоит из трех этапов.
1. [Проектирование и концепция](3d-app-launcher-design-guidance.md)
2. [Моделирование и экспорт](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Интеграция этого приложения в приложение (в этой статье)

Трехмерные ресурсы, которые будут использоваться в качестве запуска для приложения, должны быть созданы с использованием [руководств по разработке Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) для обеспечения совместимости. Активы, которые не соответствуют этой спецификации разработки, не будут подготавливаться к просмотру на домашней странице Windows Mixed Reality.

## <a name="configuring-the-3d-launcher"></a>Настройка средства запуска 3D

При создании нового проекта в Visual Studio создается простая стандартная плитка, которая отображает имя и логотип приложения. Чтобы заменить это 2D-представление на настраиваемую трехмерную модель, измените манифест приложения, включив в него элемент "Микседреалитимодел" в определении плитки по умолчанию. Чтобы вернуться к 2D-средству запуска, просто удалите определение Микседреалитимодел из манифеста.

### <a name="xml"></a>XML

Сначала необходимо указать манифест пакета приложения в текущем проекте. По умолчанию манифест будет называться Package. appxmanifest. Если вы используете Visual Studio, щелкните правой кнопкой мыши манифест в средстве просмотра решения и выберите **Просмотреть источник** , чтобы открыть XML-файл для редактирования. 

В верхней части манифеста Добавьте схему uap5 и включите ее как игнорируемое пространство имен:

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Затем укажите "Микседреалитимодел" в плитке по умолчанию для приложения:

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

Элементы Микседреалитимодел принимают путь к файлу, указывающему на трехмерный ресурс, хранящийся в пакете приложения. Сейчас поддерживаются только объемные модели, доставляемые с помощью формата файла GLBA и созданные в соответствии с [инструкциями по созданию трехмерных ресурсов Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) . Ресурсы должны храниться в пакете приложения, и анимация в настоящее время не поддерживается. Если параметр "Path" оставлен пустым, то вместо 3D-запуска будет отображаться 2D. **Примечание** . ресурс. GLBA должен быть помечен как "Content" в параметрах сборки перед сборкой и запуском приложения.


![выберите GLBA в обозревателе решений и используйте раздел Properties, чтобы пометить его как "содержимое" в параметрах сборки](images/buildsetting-content-300px.png)<br>
*Выберите GLBA в обозревателе решений и в разделе "Свойства" пометьте его как "содержимое" в параметрах сборки.*

### <a name="bounding-box"></a>Ограничивающий прямоугольник

Ограничивающий прямоугольник можно использовать, чтобы дополнительно добавить дополнительную область буфера вокруг объекта. Ограничивающий прямоугольник задается с помощью центральной точки и экстентов, которые указывают расстояние от центра ограничивающего прямоугольника до его границ вдоль каждой оси. Единицы для ограничивающего прямоугольника можно сопоставить с 1 единицей измерения. Если ограничивающий прямоугольник не указан, он будет автоматически размещается в сетке объекта. Если предоставленный ограничивающий прямоугольник меньше, чем модель, размер будет изменен в соответствии с сеткой.

Поддержка атрибута ограничивающего прямоугольника поступает вместе с обновлением Windows RS4 в качестве свойства элемента Микседреалитимодел. Чтобы сначала определить ограничивающий прямоугольник в верхней части манифеста приложения, добавьте схему uap6 и включите ее в качестве игнорируемых пространств имен:

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="https://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Затем на Микседреалитимодел задайте свойство Спатиалбаундингбокс, чтобы определить ограничивающий прямоугольник: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Использование Unity

При работе с Unity проект должен быть создан и открыт в Visual Studio, прежде чем можно будет изменить манифест приложения. 

>[!NOTE]
>При создании и развертывании нового решения Visual Studio из Unity необходимо переопределить трехмерное средство запуска в манифесте.

## <a name="3d-deep-links-secondarytiles"></a>Трехмерные глубокие ссылки (secondaryTiles)

> [!NOTE]
> Эта функция была добавлена в составе обновления 2017 (RS3) для "иммерсивное" (VR), а также в рамках обновления за Апрель 2018 (RS4) для HoloLens. Убедитесь, что приложение предназначено для версии Windows SDK больше или равно 10.0.16299 на наушниках (VR) и 10.0.17125 на HoloLens. Последнюю Windows SDK можно найти [здесь](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>Трехмерные глубокие ссылки (secondaryTiles) работают только с 2D-приложениями UWP. Однако можно создать [средство запуска для 3D-приложения](implementing-3d-app-launchers.md) , чтобы запустить эксклюзивное приложение из домашней страницы Windows Mixed Reality.

Вы можете улучшить приложения для Windows Mixed Reality, добавив возможность размещения трехмерных моделей из приложения на [домашней странице Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) в качестве глубоких ссылок на содержимое в двухмерном приложении, так же, как [2D-вторичные плитки](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) на начальном экране Windows. меню. Например, можно создать 360 °, которые непосредственно связываются с приложением 360 ° Photo Viewer, или позволить пользователям размещать трехмерное содержимое из коллекции ресурсов, открывающей страницу сведений об авторе. Это всего лишь два способа расширить функциональные возможности 2D-приложения с помощью трехмерного содержимого.

### <a name="creating-a-3d-secondarytile"></a>Создание трехмерного "Секондаритиле"

Вы можете поместить трехмерное содержимое из приложения, используя "secondaryTiles", определив модель смешанной реальности во время создания. Модели смешанной реальности создаются путем ссылки на трехмерный ресурс в пакете приложения и при необходимости определения ограничивающего прямоугольника. 

> [!NOTE]
> Создание "secondaryTiles" из монопольного представления в настоящее время не поддерживается.

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

Ограничивающий прямоугольник можно использовать для добавления дополнительной области буфера вокруг объекта. Ограничивающий прямоугольник задается с помощью центральной точки и экстентов, которые указывают расстояние от центра ограничивающего прямоугольника до его границ вдоль каждой оси. Единицы для ограничивающего прямоугольника можно сопоставить с 1 единицей измерения. Если ограничивающий прямоугольник не указан, он будет автоматически размещается в сетке объекта. Если предоставленный ограничивающий прямоугольник меньше, чем модель, размер будет изменен в соответствии с сеткой.

### <a name="activation-behavior"></a>Поведение при активации

> [!NOTE]
> Эта функция будет поддерживаться в рамках обновления Windows RS4. Убедитесь, что приложение предназначено для версии Windows SDK больше или равно 10.0.17125, если вы планируете использовать эту функцию

Вы можете определить поведение при активации трехмерного Секондаритиле, чтобы управлять тем, как оно будет реагировать, когда пользователь выберет его. Это можно использовать для размещения трехмерных объектов на домашней странице Mixed Reality, которые являются исключительно информативными или декоративными. Поддерживаются следующие типы поведения активации:
1. По умолчанию: когда пользователь выбирает 3D-Секондаритиле, что приложение активируется
2. Нет: когда пользователи выбирают 3D Секондаритиле, ничего не происходит и приложение не активируется.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Получение и обновление существующего "Секондаритиле"

Разработчики могут вернуть список существующих вторичных плиток, включающих ранее указанные свойства. Они также могут обновлять свойства, изменяя значение и вызывая UpdateAsync ().

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

Трехмерные ссылки (secondaryTiles) можно создавать только тогда, когда представление отображается на гарнитуре Windows Mixed Reality. Если представление не представлено на гарнитуре Windows Mixed Reality, рекомендуется правильно его обработать, либо скрыть точку входа, либо Показать сообщение об ошибке. Это можно проверить, выполнив запрос к [искуррентвиевпресентедонхолографик ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Уведомления на плитках

Уведомления плитки в настоящее время не поддерживают отправку обновлений в 3D-ресурс. Это означает, что разработчики не смогут выполнять следующие действия.
* Push-уведомления
* Периодическое опрос
* Запланированные уведомления

Дополнительные сведения о функциях и атрибутах других плиток, а также о том, как они используются для 2D-плиток, см. в [документации по ПРИЛОЖЕНИЯМ UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>См. также

* [Образец модели Mixed Reality](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) , содержащий средство запуска 3D-приложения.
* [Руководство по проектированию средств запуска трехмерных приложений](3d-app-launcher-design-guidance.md)
* [Создание трехмерных моделей для использования на домашней странице Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Реализация запуска трехмерных приложений (приложения Win32)](implementing-3d-app-launchers-win32.md)
* [Навигация по дому с технологией Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
