---
title: Помощи в Unity
description: Взглядом — это основной способ для пользователей для нацеливания голограммы, создаваемые приложения в смешанной реальности.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: взглядом, unity, голограмма, смешанной реальности
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604803"
---
# <a name="gaze-in-unity"></a>Помощи в Unity

[Помощи](gaze.md) является основным способом для пользователей для нацеливания [голограммы](hologram.md) ваше приложение создает в [смешанной реальности](mixed-reality.md).

## <a name="implementing-gaze"></a>Реализация взглядом

По существу [помощи](gaze.md) реализуется путем проецирования лучом, проведенным из головы пользователя, где гарнитуры, в прямом направлении их с выходом и определение, Рэй конфликтует с. В Unity пользователя головной положения и направления, предоставляются с помощью Unity Main [камеры](camera-in-unity.md), в частности [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) и [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Вызов [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) приводит [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) структуры, который содержит сведения о конфликтов, включая трехмерной точки, где возник конфликт и других GameObject луч взглядом со стенами вдоль.

### <a name="example-implement-gaze"></a>Пример. Реализуйте взглядом

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>Советы и рекомендации

Хотя в приведенном выше примере показано, как сделать один raycast, чтобы найти целевой взглядом цикл обновления, рекомендуется для этого в управлении взглядом вместо этого в любой объект, который потенциально заинтересовано в объекте gazed в один объект. Это позволяет сохранить обработки, выполнив только один raycast взглядом каждого кадра приложения.

## <a name="visualizing-gaze"></a>Визуализация взглядом

Так же, как на рабочем столе, где использовать указатель мыши выбирать и взаимодействовать с содержимым, следует реализовать [курсор](cursors.md) , представляющий взглядом пользователя. Это дает уверенность пользователей в том, что они сейчас взаимодействовать.

## <a name="gaze-in-mixed-reality-toolkit"></a>Помощи в наборе средств для смешанной реальности
При импорте [Unity пакеты выпуска MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) или клонируйте проект со страницы [репозиторий GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), нужно найти новое меню «Смешанной реальности Toolkit» в Unity. В меню «Настройка» вы увидите меню «Применить смешанной реальности сцены параметры». Если щелкнуть его, он удаляет камеры по умолчанию и добавляет основных компонентов — [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), и [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Меню MRTK для установки сцены](images/MRTK_Input_Menu.png)<br>
*Меню MRTK для установки сцены*

![Настройка автоматического сцены в MRTK](images/MRTK_HowTo_Input1.png)<br>
*Настройка автоматического сцены в MRTK*

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a>Помощи связанные скрипты в смешанной реальности Toolkit
Смешанный реальности Toolkit включает InputManager prefab [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) и [помощи стабилизатор](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs). В разделе [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), можно назначить пользовательский курсор. По умолчанию, анимировано [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) назначается.

[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) и [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) показано, как визуализировать ваш взглядом, использование курсоров.

## <a name="see-also"></a>См. также
* [Камера](camera-in-unity.md)
* [Взглядом](gaze.md)
* [Курсоры](cursors.md)
* [Нацеливание взглядом](gaze-targeting.md)
