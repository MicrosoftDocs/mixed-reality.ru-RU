---
title: Руководство по для Unity переносу входных данных
description: Узнайте, как обрабатывать входные данные для Windows смешанной реальности в Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: входные данные, unity, перенос
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602789"
---
# <a name="input-porting-guide-for-unity"></a>Руководство по для Unity переносу входных данных

Можно перенести ваши логика ввода в Windows Mixed Reality, с помощью одного из двух подходов, общие Input.GetButton/GetAxis API Unity, которые охватывают несколько платформ или XR относящиеся к Windows. WSA. Входной API-интерфейсы, которые предоставляют более подробные данные, специально для контроллеров движения и HoloLens руки.

## <a name="general-inputgetbuttongetaxis-apis"></a>API-интерфейсы Input.GetButton/GetAxis Общие

Unity в настоящее время использует его общие Input.GetButton/Input.GetAxis API-интерфейсы для предоставления входных данных для [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) и [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html). Если ваши приложения уже используют эти API-интерфейсы для входных данных, это самый простой путь для поддержки контроллеров движения в Windows Mixed Reality: следует просто необходимо переназначить осей в диспетчере ввода и кнопки.

Дополнительные сведения см. в разделе [таблицу сопоставления кнопки/оси Unity](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) и [Обзор распространенных API-интерфейсов Unity](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR относящиеся к Windows. WSA. API ввода

Если приложение уже сборка логика пользовательского ввода для каждой платформы, вы можете использовать Windows конкретных пространственных входной интерфейсы API в разделе **UnityEngine.XR.WSA.Input** пространства имен. Это позволяет получить доступ к Дополнительные сведения, например положение точности или вид источника, что позволяет сообщить HoloLens руки и контроллеры друг от друга.

Дополнительные сведения см. в разделе [Обзор API-интерфейсов UnityEngine.XR.WSA.Input](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Поза захвата для изменения и указывающего поза

Windows Mixed Reality поддерживает движения контроллеров в различных форм-факторов, дизайна каждый контроллер, отличающихся по отношению между положение руки пользователя и натуральный «переслать» направление этого приложения следует использовать для команды при подготовке к просмотру контроллер.

Чтобы лучше представить эти контроллеры, существует два вида создает изучаться для каждого источника взаимодействия:

* **Поза захвата для изменения**, представляющий расположение руку, обнаруживаемые HoloLens или palm, удерживая контроллером движения.
    * На иммерсивную, это поза лучше всего подходит для подготовки к просмотру **руку пользователя** или **объект содержится в руки пользователя**, например помехой или оружия.
    * **Возьмитесь за позиции**: Palm центроида при удержании контроллер, естественно, корректируется, влево или вправо, чтобы центрировать позиция в пределах захвата.
    * **Возьмитесь за правой оси в ориентации**: При открытии полностью свои силы для формирования позу плоских 5 палец, луч, является нормальным для вашей palm (вперед от левой palm назад от правой palm)
    * **Возьмитесь за ориентации на ось, направленная вперед**: При закрытии вашей руке частично (как будто держа контроллеру), луч, указывающий «forward» трубку, образованное пальцы отличных от бегунка.
    * **Возьмитесь за ориентации элемента вверх оси**: Ось вверх, право и прямого определения содержится в разрешении.
    * Для доступа к поза захвата для изменения входных данных между поставщиками либо Unity API (**[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) или через API Windows конкретных (**sourceState.sourcePose.TryGetPosition/Rotation**, запрашивающего поза захвата для изменения).
* **Поза указатель**, представляющий кончика контроллера, указывающего вперед.
    * Этот поза лучше всего подходит для raycast при **обращены пользовательского интерфейса** при отрисовке самой модели контроллера.
    * В настоящее время доступна только через интерфейс API, специально Windows поза указатель (**sourceState.sourcePose.TryGetPosition/Rotation**, запрашивающего поза указатель).

Эти поза координаты выражаются в мировых координатах Unity.

## <a name="see-also"></a>См. также
* [Контроллеры движения](motion-controllers.md)
* [Жестов и контроллеры движения в Unity](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Руководства по переносу](porting-guides.md)
