---
title: Включение размещения трехмерных моделей в домашней области
description: Размещение трехмерных моделей с веб-сайта или приложения на домашней странице Windows Mixed Reality
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, модель, место дома, место, мир, моделирование, Домашняя страница "смешанная реальность", Интернет, приложение
ms.openlocfilehash: 954086b79e3614e1b75ceb7560f9fc87435530fa
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829736"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Включение размещения трехмерных моделей на домашней странице смешанной реальности

> [!NOTE]
> Эта функция была добавлена как часть [обновления Windows 10 апреля 2018 г](release-notes-april-2018.md). Более старые версии Windows несовместимы с этой функцией.

[Главная страница Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) — это отправная точка, в которой пользователи начинают работу перед запуском приложений. В некоторых случаях двумерные приложения (например, приложения с голограммами) позволяют размещать трехмерные модели непосредственно в домашней среде "смешанной реальности" как украшения или для дальнейшей проверки в полном объеме. *Протокол добавления модели* позволяет отправить трехмерную модель с веб-сайта или приложения непосредственно на домашнюю страницу Windows Mixed Reality, где они будут сохраняться как средства [запуска 3D-приложений](3d-app-launcher-design-guidance.md), 2D-приложения и голограммы. 

Например, если вы разрабатываете приложение, которое охватывает каталог трехмерной мебели для создания пространства, можно использовать *Протокол добавления модели* , чтобы разрешить пользователям размещать эти модели трехмерной мебели из каталога. После помещения в мир пользователи могут перемещать, изменять размер и удалять эти трехмерные модели так же, как и другие голограммы дома. В этой статье приводятся общие сведения о реализации *протокола добавления модели* , позволяющие пользователям добавлять в мир трехмерные объекты из приложения или из Интернета.

## <a name="device-support"></a>Поддержка устройств

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Возможность</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></td>
    </tr>
     <tr>
        <td>Добавление протокола модели</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="overview"></a>Обзор

Существует два шага по включению размещения трехмерных моделей в домашней среде Windows Mixed Reality:
1. [Убедитесь, что ваша трехмерная модель совместима с домашней системой Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Реализуйте *Протокол добавления модели* в приложении или на веб-странице (в этой статье).

## <a name="implementing-the-add-model-protocol"></a>Реализация *протокола добавления модели*

После создания совместимой [трехмерной модели](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)можно реализовать *Протокол добавления модели* , активируя следующий URI с любой веб-страницы или приложения:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Если URI указывает на удаленный ресурс, он будет автоматически скачан и помещен в домашнюю страницу. Локальные ресурсы будут скопированы в папку данных приложения для дома смешанной реальности перед размещением в домашней папке. Мы рекомендуем разработать свой опыт для учета сценариев, в которых пользователь может работать под управлением более старой версии Windows, которая не поддерживает эту функцию, скрывая кнопку или отключая ее по возможности. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Вызов *протокола добавления модели* из приложения универсальная платформа Windows:

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

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Вызов *протокола добавления модели* с веб-страницы:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Рекомендации для головных телефонов (VR)

* Для головных гарнитур (VR) на портале Mixed Reality не должно выполняться никаких запусков перед вызовом *протокола добавления модели*. В этом случае *Протокол добавления модели* запустит портал Mixed Reality и поместит объект непосредственно там, где будет смотреться гарнитура, когда вы поступите на главную страницу Mixed Reality. 
* При вызове *протокола добавления модели* с рабочего стола с уже запущенным порталом Mixed Reality убедитесь, что головной телефон находится в спящем режиме. В противном случае размещение не будет выполняться. 

## <a name="see-also"></a>См. также

* [Создание трехмерных моделей для использования на домашней странице Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Навигация по дому с технологией Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
