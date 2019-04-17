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
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Включение размещения 3D-моделей в смешанной реальности home

> [!NOTE]
> Эта функция была добавлена как часть [обновления Windows 10 апреля 2018 г.](release-notes-april-2018.md). Более старые версии Windows не совместимы с помощью этой функции.

[Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) является отправной точкой, где пользователи будут располагаться перед запуском приложения. В некоторых сценариях 2D приложения (такие как голограммы) целенаправленного размещения трехмерных моделей непосредственно в домашней смешанной реальности, как оформление или для дальнейшей проверки в полностью трехмерном режиме. *Добавьте протокол модели* можно отправить к трехмерной модели из веб-сайта или приложения непосредственно в Windows Mixed Reality дома, где будет сохраняться, например [средствах запуска приложений 3D](3d-app-launcher-design-guidance.md), 2D приложения и голограммы. 

Например, если вы разрабатываете приложения который предоставляет доступ к a каталога 3D мебели по проектированию пробел, можно использовать *добавьте протокол модели* позволяет поместить этих моделей 3D мебель из каталога. После размещения в мире пользователей можно перемещать, масштабировать и удалить эти трехмерных моделей, так же, как другие голограммы домашних. В этой статье представлен обзор реализации *добавьте протокол модели* , что можно запускать разрешение пользователям снабдить их мир с трехмерными объектами из приложения или в Интернете.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Компонент</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td>Добавление протокола модели</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="overview"></a>Обзор

Разрешить размещение трехмерными моделями в Windows Mixed Reality домашней пользователю 2 этапов.
1. [Обеспечить совместимость с Windows Mixed Reality домашней 3D-модели](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Реализуйте *добавьте протокол модели* в ваше приложение или веб-страницу (в этой статье).

## <a name="implementing-the-add-model-protocol"></a>Реализация *добавьте протокол модели*

При наличии [совместимых трехмерной модели](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), можно реализовать *добавьте протокол модели* , активировав следующий URI из любой веб-страницы или приложения:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Если URI указывает на удаленном ресурсе, затем он будет автоматически быть загружается и помещается в доме. Локальные ресурсы будут скопированы в папку данных приложения смешанной реальности Домашняя до помещения в доме. Мы рекомендуем проектирование вашей работой учетной записи для сценариев, где пользователь может работать под управлением более ранней версии Windows, который не поддерживает эту функцию, скрыв кнопки или отключить его, если это возможно. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Вызов *добавьте протокол модели* из приложения универсальной платформы Windows:

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Вызов *добавьте протокол модели* на веб-странице:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Рекомендации по иммерсивную (VR)

* Для иммерсивную (VR) портале смешанной реальности не должны быть запущены перед вызовом *добавьте протокол модели*. В этом случае *добавьте протокол модели* запустится портале смешанной реальности и поместить объект непосредственно где гарнитура смотрит после появления в смешанной реальности home. 
* При вызове *добавьте протокол модели* с рабочего стола с помощью смешанной реальности портала уже выполняется, убедитесь, что гарнитура «переходит в спящий режим». В противном случае размещение не удастся. 

## <a name="see-also"></a>См. также

* [Создании трехмерных моделей для использования в домашних Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Перемещение Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)
