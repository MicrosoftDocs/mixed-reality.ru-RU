---
title: Жестов и контроллеры движения в Unity
description: Существует два основных способа действия с вашей взглядом в Unity, жестами руками и контроллеры движения.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: жесты, контроллеры движения, unity, взглядом, входные данные
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597656"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Жестов и контроллеры движения в Unity

Существует два способа ключа для выполнения действий на вашей [помощи в Unity](gaze-in-unity.md), [передать жесты](gestures.md) и [движения контроллеров](motion-controllers.md). Данные для обоих источников пространственных данных, доступный через те же интерфейсы API в Unity.

Среда Unity предоставляет два основных способа для доступа к пространственных входных данных для Windows Mixed Reality, распространенные *Input.GetButton/Input.GetAxis* API, которые работают на нескольких пакетов SDK Unity XR и *InteractionManager / GestureRecognizer* API, относящиеся к Windows Mixed Reality, который предоставляет полный набор доступных пространственных входных данных.

## <a name="unity-buttonaxis-mapping-table"></a>Таблица сопоставления кнопки/оси Unity

Идентификаторы в таблице ниже кнопку и оси, поддерживаются в Unity входных данных Manager для контроллеров движения Windows Mixed Reality через *Input.GetButton/GetAxis* API-интерфейсов, пока в столбце «Windows MR» определяемые ссылается на свойства Доступные за пределами класса *InteractionSourceState* типа. Каждый из этих API подробно описаны в следующих разделах.

Идентификатор сопоставления кнопки/оси для смешанной реальности Windows обычно соответствует Oculus кнопку/оси идентификаторы.

Идентификатор сопоставления кнопки/оси для смешанной реальности Windows отличаются от сопоставлений в OpenVR двумя способами:
1. Сопоставление использует идентификаторы сенсорной панели, которые отличаются от джойстик, для поддержки контроллеров с thumbsticks и сенсорные панели.
2. Сопоставление позволяет избежать перегрузки кнопку A и X идентификаторов кнопок меню для оставлю их для физических кнопок ABXY.

<table>
<tr>
<th rowspan="2">Ввод </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Общие интерфейсы API Unity</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Входной API конкретных Windows MR</a><br />(XR. WSA. Входные данные)</th>
</tr><tr>
<th> Слева </th><th> Справа</th>
</tr><tr>
<td> Выбор триггера нажата </td><td> 9 = 1.0 оси </td><td> 10 = 1.0 оси </td><td> selectPressed</td>
</tr><tr>
<td> Выберите значение аналогового триггера </td><td> Оси 9 </td><td> Оси 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Выбор триггера частично нажата </td><td> Кнопка 14 <i>(игровой совместимости)</i> </td><td> Кнопка 15 <i>(игровой совместимости)</i> </td><td> selectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Была нажата кнопка меню </td><td> Кнопка 6 * </td><td> Кнопка 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Была нажата кнопка захвата для изменения </td><td> Оси 11 = 1.0 (не аналоговый значения)<br />Кнопка 4 <i>(игровой совместимости)</i> </td><td> Оси 12 = 1.0 (не аналоговый значения)<br />Кнопка 5 <i>(игровой совместимости)</i> </td><td> Поняв значимость комбинирования</td>
</tr><tr>
<td> Джойстик X <i>(слева: от -1.0, справа: 1.0)</i> </td><td> Оси 1 </td><td> Оси 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Джойстик Y <i>(top: от -1.0, нижней: 1.0)</i> </td><td> Оси 2 </td><td> Оси 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Джойстик нажата </td><td> Кнопка 8 </td><td> Кнопка 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> X сенсорной панели <i>(слева: от -1.0, справа: 1.0)</i> </td><td> Оси 17 * </td><td> Оси 19 * </td><td> touchpadPosition.x</td>
</tr><tr>
<td> Y сенсорной панели <i>(top: от -1.0, нижней: 1.0)</i> </td><td> Оси 18 * </td><td> Оси 20 * </td><td> touchpadPosition.y</td>
</tr><tr>
<td> Затронутых сенсорной панели </td><td> Кнопка 18 * </td><td> Кнопка 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Нажата сенсорной панели </td><td> Кнопка 16 * </td><td> Кнопка 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> Поза 6DoF захвата для изменения или поза указатель </td><td colspan="2"> <i>Захват</i> представляют только: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></td><td> Передайте <i>захвата для изменения</i> или <i>указатель</i> как аргумент: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Отслеживание состояния </td><td colspan="2"> <i>Позиция точность источника потери риска и доступно только через интерфейс API, специально MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Эти кнопки/оси идентификаторы отличаются от используемых Unity для OpenVR из-за конфликтов в сопоставления, используемые игровые планшеты, сенсорное управление Oculus и OpenVR идентификаторы.

## <a name="grip-pose-vs-pointing-pose"></a>Поза захвата для изменения и указывающего поза

Windows Mixed Reality поддерживает движения контроллеров в различных форм-факторов, дизайна каждый контроллер, отличающихся по отношению между положение руки пользователя и натуральный «переслать» направление этого приложения следует использовать для команды при подготовке к просмотру контроллер.

Чтобы лучше представить эти контроллеры, существует два вида можно выяснить, для каждого источника взаимодействия создает **поза захвата для изменения** и **поза указатель**. Оба захвата для изменения поза и указатель поза координаты заданы все API-интерфейсами Unity в мировых координатах глобального Unity.

### <a name="grip-pose"></a>Поза захвата для изменения

**Поза захвата для изменения** представляет расположение руку, обнаруживаемые HoloLens или palm, удерживая контроллером движения.

На иммерсивную, поза захвата для изменения лучше всего подходит для подготовки к просмотру **руку пользователя** или **объект содержится в руки пользователя**, например помехой или оружия. Захват поза также используется, когда визуализация контроллером движения, как **отрисовываемые модели** предоставляемых по Windows для перемещения контроллер использует поза захвата для изменения в качестве его источника и центр вращения.

Захват поза определяется специально следующим образом:
* **Возьмитесь за позиции**: Palm центроида при удержании контроллер, естественно, корректируется, влево или вправо, чтобы центрировать позиция в пределах захвата. На контроллере Windows Mixed Reality движения этой позиции обычно выравнивает может воспользоваться кнопкой.
* **Возьмитесь за правой оси в ориентации**: При открытии полностью свои силы для формирования позу плоских 5 палец, луч, является нормальным для вашей palm (вперед от левой palm назад от правой palm)
* **Возьмитесь за ориентации на ось, направленная вперед**: При закрытии вашей руке частично (как будто держа контроллеру), луч, указывающий «forward» трубку, образованное пальцы отличных от бегунка.
* **Возьмитесь за ориентации элемента вверх оси**: Ось вверх, право и прямого определения содержится в разрешении.

Для доступа к поза захвата для изменения входных данных между поставщиками либо Unity API (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) или через интерфейс API, специально Windows MR (*sourceState.sourcePose.TryGetPosition/Rotation*, запрос представлять данные для **захвата для изменения** узла).

### <a name="pointer-pose"></a>Указатель поза

**Поза указатель** представляет собой кончик контроллера, указывающего вперед.

Поза системных указатель лучше использовать для raycast, когда вы будете **Подготовка к просмотру самой модели контроллера**. При отрисовке другого виртуального объекта вместо контроллера, такие как виртуальные оружия, должна указывать с луч, наиболее удобный для этого виртуального объекта, например луч, проходит по barrel дулом заданное приложением модели. Так как пользователи смогут просматривать виртуальным объектом и не физический контроллер, указывает с виртуальный объект будет более естественным для тех, с помощью приложения.

В настоящее время доступна в Unity только через интерфейс API, специально Windows MR, поза указатель *sourceState.sourcePose.TryGetPosition/Rotation*, передавая *InteractionSourceNode.Pointer* как аргумент.

## <a name="controller-tracking-state"></a>Состояние отслеживания контроллера

Например наушники контроллер движения Windows Mixed Reality не требует настройки внешних отслеживания датчиков. Вместо этого контроллеры отслеживаются датчики в гарнитуры, сам.

Если пользователь перемещает контроллеров из поля зрения гарнитуры, в большинстве случаев Windows будет продолжать infer позиций контроллера и предоставлять их в приложение. Когда контроллер потерял visual отслеживание достаточно, долго позиций контроллера приведет к удалению в положения приблизительное точность.

На этом этапе система будет текст с блокировкой на контроллере, чтобы пользователь, отслеживания положение пользователя по мере перемещения, во время по-прежнему предоставляя true ориентации контроллера с помощью датчиков его внутренней ориентации. Многие приложения, использующие контроллеры указывали на и активировать элементы пользовательского интерфейса можно работать в обычном режиме в точности приблизительных без каких-пользователя.

Чтобы понять, для этого рекомендуется испытать их самостоятельно. Просмотрите этот видеоролик с примерами иммерсивных содержимого, которое работает с контроллерами движения для различных состояний для отслеживания:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Рассуждения о явно отслеживания состояния

Приложения, которые желают обрабатывать позиций, иначе, основываясь на отслеживание состояния может пойти дальше и проверять состояние контроллера на свойства, например *SourceLossRisk* и *PositionAccuracy*:

<table>
<tr>
<th> Отслеживание состояния </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Высокая точность</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Высокий </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Высокая точность (риску потери)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Высокий </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Точность приблизительных</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Приблизительна </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Позиция не</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Приблизительна </td><td style="background-color: orange"> false</td>
</tr>
</table>

Эти состояния отслеживания контроллера движения, определяются следующим образом:
* **Высокая точность:** Когда движения контроллер находится в пределах гарнитура поле зрения, он предоставит обычно позиций, высокой точности, основываясь на visual отслеживания. Обратите внимание, что перемещение контроллера, сразу же оставляет поле зрения или закрывается сразу же датчиков Гарнитура (например, пользователей с другой стороны) продолжит возвращать создает высокой точности на короткое время, в зависимости от инерционного отслеживания контроллера сам.
* **Высокая точность (риску потери):** При перемещении контроллера движения за край поле зрения гарнитуры, гарнитура скоро будет может визуально отслеживать положение контроллера. Приложение знает, когда контроллер достиг эту FOV границу, достаточно **SourceLossRisk** достичь 1.0. На этом этапе приложение можно приостановить контроллера жесты, требующих устойчивый поток создает очень высокого качества.
* **Точность приблизительных:** Когда контроллер потерял visual отслеживание достаточно, долго позиций контроллера приведет к удалению в положения приблизительное точность. На этом этапе система будет текст с блокировкой на контроллере, чтобы пользователь, отслеживания положение пользователя по мере перемещения, во время по-прежнему предоставляя true ориентации контроллера с помощью датчиков его внутренней ориентации. Многие приложения, использующие контроллеры указывали на и активировать элементы пользовательского интерфейса может работать как обычный while в точности приблизительных без каких-пользователя. Приложений с помощью более дешевые требования к входным данным, можно находить спад из **высокой** точность до одной **приблизительно** точности, проверяя **PositionAccuracy** свойство, для Пример для предоставления пользователю более масштабны hitbox на целевые объекты вне экрана в течение этого времени.
* **Позиция не:** Пока контроллер может работать в точности приблизительных в течение длительного времени, иногда система знает, что даже позицию заблокирован для текста не имеет смысла в данный момент. Например контроллер, который просто был включен может никогда не наблюдались визуально или пользователь может поместить работу контроллера, который затем передается другим пользователем. В эти моменты времени, система не будет предоставлять любой позиции в приложение и *TryGetPosition* возвратит значение false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>Общие интерфейсы API Unity (Input.GetButton/GetAxis)

**Пространство имен:** *UnityEngine*, *UnityEngine.XR*<br>
**Типы**: *Входные данные*, *XR. InputTracking*

Unity в настоящее время использует общего *Input.GetButton/Input.GetAxis* API-интерфейсы для предоставления входных данных для [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) и смешанной реальности Windows, включая руки и контроллеры движения. Если ваше приложение использует эти API-интерфейсы для входных данных, его можно легко поддерживать контроллеры движения нескольких пакетов SDK XR, в том числе Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Получение логического кнопка нажата

Чтобы использовать общие интерфейсам API ввода Unity, вы обычно начнем с подключения кнопки и осей для логические имена в [диспетчер ввода Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), привязка к имени каждой кнопки или оси идентификаторы. Затем можно написать код, который ссылается на это имя логического кнопку/оси.

Например, чтобы сопоставить кнопка слева движения контроллера триггера действие отправки, перейдите к **изменить > Параметры проекта > ввода** в Unity и разверните свойства разделе отправить осей. Изменение **положительным кнопку** или **положительное кнопку Alt** свойство для чтения **кнопку джойстика 14**, следующим образом:

![Unity InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

Скрипт затем можно установить флажок для действия отправки с помощью *Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Можно добавить более логичным кнопки, изменив **размер** свойства в разделе **осей**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Начало физической кнопки нажаты напрямую

Можно также открыть кнопки вручную, их полное доменное имя, используя *Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Получение руки или поза движения контроллера

Можно получить доступ к положения и поворота контроллера, с помощью *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Обратите внимание, что это относится к поза захвата для изменения контроллера (когда пользователь удерживает контроллеру), что полезно для подготовки к просмотру помехой или дулом в пользователя вручную, или модель сам контроллер.

Обратите внимание на то, что связь между этой поза захвата для изменения и позу указатель (куда указывает кончика контроллеру), могут отличаться между контроллерами. В данный момент доступ к поза указателя контроллера можно только посредством ввода MR конкретных API, описанные в следующих разделах.

## <a name="windows-specific-apis-xrwsainput"></a>Windows API-интерфейсам конкретной (XR. WSA. Входные данные)

**Пространство имен:** *UnityEngine.XR.WSA.Input*<br>
**Типы**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*,  *InteractionSourceKind*, *InteractionSourceLocation*

Чтобы получить более подробные сведения о наличии входных данных в Windows Mixed Reality (для HoloLens) и контроллеры движения, вы можете использовать Windows пространственных входной API-интерфейсам конкретной в разделе *UnityEngine.XR.WSA.Input* пространства имен. Это позволяет получить доступ к Дополнительные сведения, например положение точности или вид источника, позволяя определить руки и контроллеры друг от друга.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Опрос состояния руки и контроллеры движения

Можно выполнить опрос для этого кадра состояния для каждого источника (вручную или движения контроллер) взаимодействия с помощью *GetCurrentReading* метод.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Каждый *InteractionSourceState* вы получаете назад представляет источник взаимодействия в текущий момент времени. *InteractionSourceState* предоставляет сведения, такие как:
* Который [виды нажатия](motion-controllers.md) происходят (Select/меню/коммерческих тайн/сенсорной панели/джойстик)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Другие данные, относящиеся к движения контроллеров, такие сенсорной панели и/или джойстик координатами x и y и изменять состояние

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* InteractionSourceKind знать, если источником является руки или контроллер движения

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Запрос создает прогноз вперед отрисовки

* При опросе с целью взаимодействия исходных данных от руки и контроллеры, создает, которые можно получить, создает прогноз вперед в данный момент времени, когда этого кадра photons достигнет глаза пользователя.  Создает эти прогнозируемые вперед лучше всего подходят для **отрисовки** контроллера или принудительное объекта каждого кадра.  Предназначенные для заданного press или выпуска с контроллером, которые будут наиболее точным, если вы используете событие журнала API, описанные ниже.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Также можно получить головной поза, прогнозируемые вперед для этого текущего кадра.  Как с помощью источника поза, это полезно для **отрисовки** a курсора, несмотря на то, что приложение предназначено для заданного press или выпуска будет наиболее точным, если вы используете событие журнала API, описанные ниже.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Обработка событий источника взаимодействия

Для обработки входных событий, происходящих с их точным поза исторических данных, можно обрабатывать события источника взаимодействия вместо опроса.

Для обработки взаимодействия источника событий:
* Зарегистрируйтесь для *InteractionManager* входного события. Для каждого типа событий взаимодействия, которые вас интересуют необходимо подписаться на него.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* Обработайте событие. Как только вы подписаны на события взаимодействия, вы получите обратного вызова, когда это необходимо. В *SourcePressed* примере это будет после был обнаружен источник, и до выпуска или потеряно.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Остановка обработки события

Необходимо остановить обработку событие, когда вы больше не интересует события или уничтожается объект, который подписался на событие. Для остановки обработки события, можно отменить подписку на событие.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Список событий источника взаимодействия

Возможное взаимодействие источника события включают:
* *InteractionSourceDetected* (источник становится активным)
* *InteractionSourceLost* (становится неактивным)
* *InteractionSourcePressed* (tap, нажатие кнопки или «Выберите» распространенная)
* *InteractionSourceReleased* (конец tap, кнопка или конец «Выбрать» распространенная)
* *InteractionSourceUpdated* (перемещение или в противном случае изменения определенного состояния)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>События для исторических создает выбора целевой платформы, которые наиболее точно соответствуют press или выпуска

Опрос API, описанные ранее Присвойте приложению создает прогноз вперед.  Хотя эти прогнозируемое создает лучше всего подходят для подготовки к просмотру контроллера или виртуальный объект handheld, будущих создает не являются оптимальными для нацеливания, по двум основным причинам:
* Когда пользователь нажимает кнопку на контроллере, может быть около 20 мс задержки беспроводной через Bluetooth прежде, чем система получает клавишу.
* Затем, если вы используете позу прогнозируемые вперед, существует другой 10-20 мс прямой прогноза применялся к целевое время, когда текущий кадр photons достигнет глаза пользователя.

Это означает, что опроса дает позу источника или head представляют то есть 30-40 мс вперед от head и руки пользователя фактически зависимостью обратно в том случае, когда произошло press или выпуска.  HoloLens входных данных вручную хотя без задержки беспроводной передачи есть аналогичные задержки для обнаружения нажатия.

Чтобы точно целевой объект на основании исходное намерение пользователя для нажатие вручную или контроллера, следует использовать поза исторических источника или головного поза, *InteractionSourcePressed* или *InteractionSourceReleased* входного события.

Вы можете целевой пресс или выпуска с поза исторические данные из головы пользователя или свой контроллер:
* Произошла головной поза на данный момент времени, когда жест или контроллера нажмите клавишу, который может использоваться для **нацеливания** для определения того, что пользователь выполнял [gazing](gaze.md) в:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* Произошла поза источника на момент времени, при контроллером движения клавиши, который может использоваться для **нацеливания** для определения того, что пользователь указывал на контроллер.  Это будет состояние контроллера, в которых прессе.  При отрисовке сам контроллер, вы можете запросить поза указатель, а не поза захвата для изменения, прострелить нацеливания лучом, проведенным из что пользователь сочтет естественным кончика, подготовке к просмотру контроллера:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Пример обработчики событий

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>Высокоуровневые составного жест API-интерфейсы (GestureRecognizer)

**Пространство имен:** *UnityEngine.XR.WSA.Input*<br>
**Типы**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

Приложение также может распознавать более высокого уровня составные жесты для пространственных источников входных данных, касание, удержание, управления и навигации жестов. В обоих сценариях можно распознать эти составные жесты [руки](gestures.md) и [движения контроллеров](motion-controllers.md) с помощью GestureRecognizer.

Каждое событие жестов на GestureRecognizer предоставляет SourceKind для входных данных, а также определения луч головного во время события. Некоторые события предоставляют дополнительные определенные сведения о контексте.

Существует лишь несколько действий, необходимых для записи с помощью распознавателя жестов:
1. Создать новый распознаватель жестов
2. Укажите, какие "действия" для отслеживания
3. Подписаться на события для этих жестов
4. Начать захват жесты

### <a name="create-a-new-gesture-recognizer"></a>Создать новый распознаватель жестов

Чтобы использовать *GestureRecognizer*, необходимо создать *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Укажите, какие "действия" для отслеживания

Укажите, какие "действия" вы заинтересованы в через *SetRecognizableGestures()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Подписаться на события для этих жестов

Подписаться на события для жестов, которые вас интересуют.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>Жесты перехода и обработки являются взаимоисключающими для экземпляра *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Начать захват жесты

По умолчанию *GestureRecognizer* не отслеживает входных данных до *StartCapturingGestures()* вызывается. Возможно, что событие жест может быть сформировано после *StopCapturingGestures()* вызывается, если входные данные была создана до кадра где *StopCapturingGestures()* был обработан. *GestureRecognizer* запоминают ли было включить или отключить во время previou кадра, в котором жест действительно выполнены и таким образом надежен, для запуска и остановки мониторинга жест с использованием нацеливания взглядом этого кадра.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Остановка отслеживания жесты

Чтобы остановить распознавания жестов:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Удаление распознаватель жестов

Не забудьте отменить подписку на события подписки перед удалением *GestureRecognizer* объекта.

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Подготовка к просмотру модели контроллера движения в Unity

![Модель контроллера движения и teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*Модель контроллера движения и teleportation*

Для подготовки к просмотру движения контроллеров в приложении, которые соответствуют физических контроллеров пользователей удерживают и сформулировать, как различные кнопки, можно использовать **MotionController prefab** в [смешанной реальности Toolkit ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Этого готового блока динамически загружает правильные glTF модели во время выполнения из драйвера контроллера установленных движения системы.  Очень важно для динамической загрузки этих моделей, а не импортируя их вручную в редакторе, что приложение будет отображать физически точные трехмерные модели какие-либо контроллеры, текущие и будущие пользователи могут иметь.

1. Выполните [Приступая к работе](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) инструкции по загрузке смешанной реальности Toolkit и добавьте его в проект Unity.
2. Если Вы заменили камеры с *MixedRealityCameraParent* prefab как часть действия Приступая к работе, вы готовы к работе!  Этого готового блока включает отрисовки контроллера движения.  В противном случае добавьте *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* сцены из области проекта.  Необходимо добавить как дочерний независимо от родительского объекта prefab использовать для перемещения камеры вокруг при teleports пользователя внутри сцены, таким образом, чтобы контроллеры поставляются вместе с пользователем.  Если приложение не включает teleporting, просто добавьте готового блока в корне сцены.

## <a name="throwing-objects"></a>Создание объектов

Создание объектов в виртуальной реальности проблема сложнее, а затем может поначалу показаться. Как и в случае с наиболее физически на основе взаимодействия, при генерации в игры действует непредвиденным образом, он совершенно очевидно и разбивает погружения. Мы потратили некоторое времени на размышления глубоко о том, как для представления физически правильное поведение создает исключение и получили рекомендации, с помощью обновления нашей платформы, который мы хотели бы поделиться с вами.

Вы найдете пример как корпорация Майкрософт рекомендует реализовать генерации [здесь](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Этот пример эти четыре рекомендации:
* **Использование контроллера *скорости* вместо позиции**. В ноябрьском обновлении для Windows, мы представили изменение в поведении при работе в ['' приблизительное '' позиционные отслеживания состояния](motion-controllers.md#controller-tracking-state). В этом состоянии скорости сведения о контроллере продолжит возвращаются до тех пор, пока мы считаем, что он является высокая точность, это часто бывает больше времени, чем позиция остается высокой точности.
* **Включить *угловую скорость* контроллера**. Эта логика находится в `throwing.cs` файл `GetThrownObjectVelAngVel` статический метод, в пакете ссылки выше:
   1. Как угловую скорость сэкономленная, созданный объект должен поддерживать же угловую скорость, как оно было в момент, когда исключение: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Как центру массы вызванного объекта, вероятно, не в начале координат поза захвата для изменения, Да, скорее всего различные скорости то контроллера в отсчета пользователя. Часть объекта скорости, использованных в этом случае является мгновенно тоже скорость центру массы вызванного объекта вокруг начала координат контроллера. Это тоже скорость составляет перекрестное произведение угловую скорость контроллера с помощью вектора, представляющего расстояние между контроллера-источником и центру массы созданный объект.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. Общая скорость вызванного объекта, таким образом, сумма скорости контроллера и это тоже скорость: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Обратите внимание на *время* по которому мы применяем скорость**. При нажатии кнопки, может занять до 20 мс для этого события всплывать через Bluetooth в операционную систему. Это означает, что если опрос для изменения состояния контроллера из клавиш для не нажата или наоборот, сведения о контроллере поза, получаемых с ним будет заранее это изменение в состоянии. Кроме того поза контроллера, представленный наших опроса API вперед вычисляется в соответствии с вероятностью поза во время отображения кадр, что в будущем может быть более 20 мс, затем. Это хороший вариант для *отрисовки* сохраняться объекты, но приводит к увеличению наша проблема времени для *нацеливания* объект как мы вычисляем траектория в данный момент пользователь отпустил их throw. К счастью, с ноябрьского обновления, когда события Unity, например *InteractionSourcePressed* или *InteractionSourceReleased* отправляется, в том числе поза исторические данные от обратно, когда кнопки был фактически нажатом или выпущенные.  Чтобы получить наиболее точные визуализации контроллера и предназначенных для контроллера во время создает исключение, необходимо правильно использовать опроса и обработки событий, соответствующим образом:
   * Для **отрисовки контроллера** каждого кадра, приложения следует располагать контроллера *GameObject* на контроллере прогнозируемые вперед представлять время photon текущего кадра.  Получить данные из Unity опроса API, такими как *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* или  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Для **нацеливания контроллера** по press или выпуска, ваше приложение должно raycast и вычислить траекторий, в зависимости от поза исторических контроллера для данного события, нажмите клавишу "или" выпуск.  Получить данные из событий Unity API-интерфейсы, такие как  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Использовать поза захвата для изменения**. Относительно поза захвата для изменения, а не указатель поза выводятся угловую скорость и скорости.

Генерация будет продолжать улучшать в последующих обновлениях Windows, и вы сможете найти дополнительную информацию о них здесь.

## <a name="accelerate-development-with-mixed-reality-toolkit"></a>Ускорение разработки с помощью смешанной реальности Toolkit

Существуют две сцены пример о InputManager и MotionController в Unity. Через эти сцен рассказывается, как InputManager MRTK доступ к данных обработки событий с помощью кнопок перемещения контроллера.

- [HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [Технические сведения в файле README](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

![Пример входных данных сцен в MRTK](images/MRTK_ExampleScene_Input.png)<br>
*Пример входных данных сцен в MRTK*

### <a name="automatic-scene-setup"></a>Настройка автоматического сцены

При импорте [Unity пакеты выпуска MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) или клонируйте проект со страницы [репозиторий GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), нужно найти новое меню «Смешанной реальности Toolkit» в Unity. В меню «Настройка» вы увидите меню «Применить смешанной реальности сцены параметры». Если щелкнуть его, он удаляет камеры по умолчанию и добавляет основных компонентов — [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), и [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Меню MRTK для установки сцены](images/MRTK_Input_Menu.png)<br>
*Меню MRTK для установки сцены*

![Настройка автоматического сцены в MRTK](images/MRTK_HowTo_Input1.png)<br>
*Настройка автоматического сцены в MRTK*

### <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefab

Их можно также вручную добавить из панели «проект». Эти компоненты можно найти как prefabs. При поиске **MixedRealityCamera**, можно увидеть два различных камеры prefabs. Разница в том, **MixedRealityCamera** только в том случае камеры prefab в то время как **MixedRealityCameraParent** включает дополнительные компоненты для иммерсивную, например Teleportation движения Контроллер и границ.

![Плоскости камеры MRTK](images/MRTK_HowTo_Input2.png)<br>
*Плоскости камеры MRTK*

**MixedRealtyCamera** поддерживает HoloLens и иммерсивных гарнитуры. Он определяет тип устройства и оптимизирует такие свойства как очистить флаги и Skybox. Далее представлены некоторые полезные свойства можно настроить, например пользовательский курсор, контроллер движения модели и Floor.

![Свойства для контроллера движения курсора и Floor](images/MRTK_HowTo_Input3.png)<br>
*Свойства для контроллера движения курсора и Floor*

## <a name="follow-along-with-tutorials"></a>Следуйте указаниям, разрабатывая учебники

Пошаговые руководства с более подробные Примеры настроек, доступны в академии реальности Mixed:

- [Входные данные MR 211: Жест](holograms-211.md)
- [Входные данные MR 213: Контроллеры движения](mixed-reality-213.md)

[![Г-н ввода 213 - контроллера движения](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Г-н ввода 213 - контроллера движения*

## <a name="see-also"></a>См. также

* [Жесты](gestures.md)
* [Контроллеры движения](motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [InteractionInputSource.cs в MixedRealityToolkit Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
