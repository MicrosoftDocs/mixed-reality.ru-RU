---
title: Входные данные MR 213
description: Этот учебник кодирования с помощью Unity, Visual Studio и иммерсивную Дополнительные сведения о контроллерах движения.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit-unity, создающий эффект присутствия, движения контроллера, academy, учебник
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604703"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br>

# <a name="mr-input-213-motion-controllers"></a>Входные данные MR 213: Контроллеры движения

Контроллеры движения в мире смешанной реальности добавьте еще один уровень интерактивности. С помощью [движения контроллеры](motion-controllers.md), мы может напрямую взаимодействовать с объектами более естественным образом, аналогичную наших физических взаимодействий в реальной жизни, увеличение общения и удовлетворения запросов в интерфейсе приложения.

В MR входной 213 мы рассмотрим входных событий контроллера движения, создавая возможность простого пространственных рисования. С этим приложением пользователям можно рисовать в трехмерном пространстве с различными типами кистей и цвета.

## <a name="topics-covered-in-this-tutorial"></a>Разделы, которые описаны в этом руководстве

|![Элемент1 MixedReality213](images/mr213-topic1.png)|![Элемент2 MixedReality213](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Контроллер визуализации**|**События ввода контроллера**|**Настраиваемый контроллер и пользовательского интерфейса**|
|Узнайте, как для подготовки к просмотру модели контроллера движения в режима игры Unity и среды выполнения.|Понять различные виды событий кнопки и их приложения.|Узнайте, как наложение элементов пользовательского интерфейса на основе контроллера или полностью настроить его.|

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td>Входные данные MR 213: Контроллеры движения</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>Предварительные требования

Контрольный список установки для иммерсивную см. в разделе на [эту страницу](install-the-tools.md).

* В этом руководстве требуется [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Файлы проекта

* [Загрузите файлы](https://github.com/Microsoft/MixedReality213/archive/master.zip) требуемые для проекта и извлеките файлы на рабочий стол.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Программа установки Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Цели

* Оптимизация разработки Unity для Windows Mixed Reality
* Программа установки смешанной реальности камера
* Настройка среды

### <a name="instructions"></a>Инструкция

* Запустите Unity.
* Выберите **откройте**.
* Перейдите к рабочего стола и найти **MixedReality213-master** папки, которые вы ранее архиве.
* Щелкните элемент **Выбор папки**.
* По завершении загрузки файлов проекта Unity можно см. в разделе редактора Unity.
* В Unity, выберите **файл > Параметры сборки**.

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* Выберите **универсальной платформы Windows** в **платформы** списке и нажмите кнопку **переключить платформу** кнопки.
* Задайте целевое устройство **любого устройства**
* Задайте тип сборки **D3D**
* Установить пакет SDK **самую новую установленную**
* Проверьте **Unity C# проектов**
    * Это позволяет изменять файлы скриптов в проект Visual Studio без повторной сборки проекта Unity.
* Нажмите кнопку **параметры проигрывателя**.
* В **инспектор** прокрутите вниз до нижней панели
* В параметрах XR проверьте **поддерживается виртуальной реальности**
* Установите пакеты SDK для виртуальной реальности **Windows Mixed Reality**

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* Закрыть **параметры построения** окна.

### <a name="project-structure"></a>Структура проекта

В этом руководстве используется  **[смешанной реальности Toolkit — Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**. Вы можете найти выпуски на [эту страницу](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Завершенные сцен для справки**
* Вы найдете двумя сценами завершенного Unity под **сцены** папки.
    * **MixedReality213**: Завершенные сцены с помощью одной кисти
    * **MixedReality213Advanced**: Завершено сцены для разработки с помощью нескольких кистей

**Новые параметры установки сцены для учебника**
* В Unity, нажмите кнопку **файл > создать сцену**
* Удалить **главной камеры** и **направленный свет**
* Из **панель проекта**, найдите и перетащите следующие prefabs в **иерархии** панели:
    * Активы/HoloToolkit/входныеданные/Prefabs/**MixedRealityCamera**
    * Активы/AppPrefabs/**среды**

![Камеры и среды](images/mr213-cameraenvironment-300px.jpg)
* Существует две плоскости камеры смешанной реальности Toolkit:
    * **MixedRealityCamera.prefab**: Только камеры
    * **MixedRealityCameraParent.prefab**: Камера + Teleportation + границ
    * В этом руководстве мы будем использовать **MixedRealityCamera** без teleportation функции. По этой причине мы добавили простой **среды** готового блока, содержащего основные floor, чтобы назначить пользователя чувствовать основе точных.
    * Дополнительные сведения о teleportation с **MixedRealityCameraParent**, см. в разделе [Advanced конструктора - Teleportation и locomotion](#advanced-design---teleportation-and-locomotion)

**Программа установки skybox**
* Нажмите кнопку **окно > освещения > Параметры**
* Щелкните этот кружок в правой части **поле материал Skybox**
* Введите в «gray» и выберите **SkyboxGray**

(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

![Параметр skybox](images/mr123-skyboxsetting-400px.jpg)
* Проверьте **Skybox** параметр, чтобы иметь возможность см. в разделе назначенный серый градиента skybox

![Переключателя skybox](images/mr213-skyboxcheck-400px.jpg)
* Сцены с MixedRealityCamera, окружающей среде и серый skybox будет выглядеть следующим образом.

![MixedReality213 среды](images/mr213-environment-600px.jpg)
* Нажмите кнопку **файл > Сохранить сцену как**
* **Сохранить** в сцену в папке сцены с любым именем

## <a name="chapter-1---controller-visualization"></a>Глава 1 - контроллера визуализации

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Цели

* Узнайте, как для подготовки к просмотру движения контроллера моделей в режиме игр Unity, а также во время выполнения.

Windows Mixed Reality предоставляет модель анимированных контроллера для контроллера визуализации. Существует несколько подходов, которые можно предпринять для визуализации контроллера в приложении:
* По умолчанию — с помощью контроллера по умолчанию без изменений
* Гибридные - с помощью контроллера по умолчанию, но настройка некоторые элементы или наложенной компонентов пользовательского интерфейса
* Замена — с использованием собственных настроенного трехмерной модели для контроллера

В этой главе будет рассказано о примерах настройки контроллера.

### <a name="instructions"></a>Инструкция

* В **проекта** панели, введите **MotionControllers** в поле поиска. Его также можно найти в разделе ресурсов/HoloToolkit/входные данные/Prefabs /.
* Перетащите **MotionControllers** prefab в **иерархии** панели.
* Щелкните **MotionControllers** prefab в **иерархии** панели.

**MotionControllers prefab**

**MotionControllers** имеет prefab **MotionControllerVisualizer** сценарий, который предоставляет слотов для моделей альтернативный контроллер. Если назначить собственные пользовательские трехмерных моделей, например руки или помехой и проверьте «Всегда использовать альтернативный влево/вправо модель», вы увидите их вместо модели по умолчанию. Мы будем использовать этот слот в главе 4 для замены модель контроллера с помощью кисти.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Инструкции**
* В **инспектор** панели, дважды щелкните **MotionControllerVisualizer** скрипт, чтобы просмотреть код в Visual Studio

**Сценарий MotionControllerVisualizer**

**MotionControllerVisualizer** и **MotionControllerInfo** классы предоставляют средства для доступа к & изменения моделей контроллера по умолчанию. **MotionControllerVisualizer** подписывается на Unity **InteractionSourceDetected** событий и автоматически создает экземпляр контроллера моделей, при их обнаружении.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Модели контроллера доставляются в соответствии с [спецификации glTF](https://github.com/KhronosGroup/glTF). Этот формат будет создана для предоставления общий формат, в то же время улучшает процесс передачи и распаковке трехмерных ресурсов. В этом случае нам нужно получить и загружать модели контроллера во время выполнения, как мы хотим сделать максимально эффективным интерфейс пользователя, а не гарантируется контроллеров движения пользователя может используемой версии. Этот курс, через набор средств смешанной реальности, использует версию группе Khronos [UnityGLTF проекта](https://github.com/KhronosGroup/UnityGLTF).

После доставки контроллер, можно использовать скрипты **MotionControllerInfo** найти преобразований для элементов определенного контроллера, чтобы они правильно определения своих положений.

В следующей главе мы узнаете, как использовать эти сценарии для присоединения к контроллерам элементы пользовательского интерфейса.

*В некоторых сценариях, вы найдете блоки кода с **#if! UNITY_EDITOR** или **UNITY_WSA**. Эти блоки кода выполняются только на UWP среды выполнения, при развертывании Windows. Это обусловлено набор API-интерфейсов, используемых в редакторе Unity и среда выполнения приложений универсальной платформы Windows, отличаются.*
* **Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки.

Можно видеть сцены с контроллерами движения в вашей гарнитуры. Вы увидите подробные анимации для нажатия кнопки, джойстик перемещения и выделение touch сенсорной панели.

![По умолчанию MR213_Controller визуализации](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Глава 2 - присоединение элементы пользовательского интерфейса к контроллеру

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Цели

* Дополнительные сведения об элементах перемещения контроллеров
* Узнайте, как для присоединения объектов к определенной части контроллеров

В этой главе вы узнаете, как добавить элементы пользовательского интерфейса в контроллер, который пользователь может легко получать доступ и изменить в любое время. Также вы узнаете, как добавить простой палитра пользовательского интерфейса с использованием сенсорной панели ввода.

### <a name="instructions"></a>Инструкция

* В **проекта** панели, поиска **MotionControllerInfo** скрипта.
* В результатах поиска щелкните дважды щелкните **MotionControllerInfo** скрипт, чтобы просмотреть код в Visual Studio.

**Сценарий MotionControllerInfo**

Первым делом необходимо решить, какой элемент контроллера вы пользовательского интерфейса для присоединения к. Эти элементы определены в **ControllerElementEnum** в **MotionControllerInfo.cs**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* **Домашняя**
* **Меню**
* **Возьмитесь**
* **Джойстик**
* **Выберите**
* **Сенсорная панель**
* **Указывающего поза** — этот элемент представляет собой кончик контроллера, указывающего направление вперед.

**Инструкции**
* В **проекта** панели, поиска **AttachToController** скрипта.
* В результатах поиска щелкните дважды щелкните **AttachToController** скрипт, чтобы просмотреть код в Visual Studio.

**Сценарий AttachToController**

**AttachToController** скрипт предоставляет простой способ для присоединения объектов к указанному контроллеру рабочей руки пользователя и элемента.

В **AttachElementToController()**,
* Проверьте рабочей руки пользователя с помощью **MotionControllerInfo.Handedness**
* Получить конкретный элемент массива контроллере, используя **MotionControllerInfo.TryGetElement()**
* После получения этого элемента преобразования из родительского объекта, находящегося под его модель контроллера и имеет нулевое значение локального положения и поворота объекта.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

Самый простой способ использования **AttachToController** сценарий должен наследовать его, как мы делали в случае использования **ColorPickerWheel.** Просто заменить **OnAttachToController** и **OnDetatchFromController** функции для выполнения установки / декомпозиции, когда контроллер были обнаружены и отключены.

**Инструкции**
* В **проекта** панели, введите в поле поиска **ColorPickerWheel**. Его также можно найти в разделе ресурсов/AppPrefabs /.
* Перетащите **ColorPickerWheel** prefab в **иерархии** панели.
* Нажмите кнопку **ColorPickerWheel** prefab в **иерархии** панели.
* В **инспектор** панели, дважды щелкните **ColorPickerWheel** скрипт, чтобы просмотреть код в Visual Studio.

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

**Сценарий ColorPickerWheel**

Так как **ColorPickerWheel** наследует **AttachToController**, он показывает **рабочей руки пользователя** и **элемент** в  **Инспектор** панели. Мы будет прикреплен пользовательский Интерфейс к элементу на сенсорной панели на левой контроллере.

![Сценарий ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** переопределяет **OnAttachToController** и **OnDetatchFromController** подписаться на событие ввода, который будет использоваться в следующей главе для выбранного цвета с сенсорной панели ввода.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* **Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки.

**Альтернативный метод для присоединения объектов к контроллерам**

Мы рекомендуем, чтобы сценарии наследовать от **AttachToController** и переопределить **OnAttachToController**. Тем не менее это может не всегда возможно. Альтернативы является использование его в качестве отдельного компонента. Это может быть полезно, если вы хотите подключить существующий готового блока к контроллеру без оптимизации кода скриптов. Просто иметь класс ожидания IsAttached будет присвоено значение true, если перед выполнением каких-либо настроек. Самый простой способ сделать это — с помощью соподпрограмме для «Start».

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Глава 3 - Работа с входными данными для сенсорной панели

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Цели

* Узнайте, как получить события входных данных на сенсорной панели
* Узнайте, как использовать сведения о положении оси сенсорной панели для работы приложения

### <a name="instructions"></a>Инструкция

* В **иерархии** панели, щелкните **ColorPickerWheel**
* В **инспектор** панели **Animatior**, дважды щелкните **ColorPickerWheelController**
* Можно видеть **Animator** откроется вкладка

**Отображение/скрытие пользовательского интерфейса с помощью Unity контроллер анимации**

Для отображения и скрытия **ColorPickerWheel** пользовательского интерфейса с помощью анимации мы используем [системы анимации Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Установка **ColorPickerWheel** **Visible** значение true или false триггеры **Показать** и **скрыть** триггеров анимации. **Показать** и **скрыть** параметры определяются в **ColorPickerWheelController** контроллер анимации.

![Контроллер анимации Unity](images/mr123-animationcontroller-550px.jpg)

**Инструкции**
* В **иерархии** панели, выберите **ColorPickerWheel** prefab
* В **инспектор** панели, дважды щелкните **ColorPickerWheel** скрипт, чтобы просмотреть код в Visual Studio

**Сценарий ColorPickerWheel**

**ColorPickerWheel** подписывается на Unity **InteractionSourceUpdated** событий для прослушивания событий сенсорной панели.

В **InteractionSourceUpdated()**, сценарий сначала проверяет, убедитесь, что он:
* фактически событие сенсорная панель (obj.state. **touchpadTouched**)
* исходит от левой контроллера (obj.state.source. **рабочей руки пользователя**)

Если выполняются оба условия, поместите сенсорной панели (obj.state. **touchpadPosition**) назначается **selectorPosition**.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

В **Update()**, основываясь на **видимым** свойство, оно активирует отображает или скрывает триггеров анимации в компоненте animator палитра цветов

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

В **Update()**, **selectorPosition** используется для приведения в сетке collider цветовой круг, который возвращает позицию UV луча. Это положение можно найти пикселя с координатой и значение цветовой круг текстуры цвета. Это значение доступно для других сценариев с помощью **SelectedColor** свойство.

![Точные точки для отслеживания колесика средство выбора цвета](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Глава 4 – переопределение модель контроллера

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Цели

* Дополнительные сведения о переопределении модель контроллера с помощью пользовательских трехмерной модели.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Инструкция

* Нажмите кнопку **MotionControllers** в **иерархии** панели.
* Щелкните этот кружок в правой части **альтернативный контроллер правой** поля.
* Введите в **"BrushController**" и выберите взята из результата. Его можно найти в разделе ресурсов/AppPrefabs/**BrushController**.
* Проверьте **всегда использовать альтернативный оптимальной модели**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**BrushController** готового блока не обязательно должен быть включены в **иерархии** панели. Тем не менее чтобы извлечь его дочерними компонентами:
* В **проекта** панели, введите в **BrushController** и перетащите **BrushController** prefab в **иерархии** панели.

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Вы найдете **совет** компонент в **BrushController**. Мы будем использовать его преобразование, запуска и остановки рисования линии.
* Удалить **BrushController** из **иерархии** панели.
* **Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки. Можно увидеть, что модель кисть замены контроллера правой движения.

## <a name="chapter-5---painting-with-select-input"></a>Глава 5 - Рисование с помощью Select входных данных

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Цели

* Сведения об использовании событий кнопки "выбрать" для запуска и остановки рисования линии

### <a name="instructions"></a>Инструкция

* Поиск **BrushController** prefab в **проекта** панели.
* В **инспектор** панели, дважды щелкните **BrushController** скрипт, чтобы просмотреть код в Visual Studio

**Сценарий BrushController**

**BrushController** подписывается на InteractionManager **InteractionSourcePressed** и **InteractionSourceReleased** события. Когда **InteractionSourcePressed** событие активируется, кисти **рисования** свойство имеет значение true; в то время, когда **InteractionSourceReleased** событие активируется, кисти **Рисования** свойство имеет значение false.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

Хотя **рисования** имеет значение true, кисть, которая будет создавать точки в созданный экземпляр Unity **LineRenderer**. Ссылку на этот готового блока хранится в кисти **Stroke Prefab** поля.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

Чтобы использовать выбранный цвет из палитры цветовой круг пользовательского интерфейса, **BrushController** должен иметь ссылку на **ColorPickerWheel** объекта. Так как **BrushController** prefab создается во время выполнения в качестве замены контроллера, необходимо задать во время выполнения все ссылки на объекты на сцене. В этом случае мы используем **GameObject.FindObjectOfType** искомого **ColorPickerWheel**:

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* **Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки. Можно для рисования линий и рисования с помощью кнопки "выбрать" на контроллере справа.

## <a name="chapter-6---object-spawning-with-select-input"></a>Объект, запускающая с выбранными ввода Глава 6.

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Цели

* Использование Select и понять входных событий для кнопки
* Узнайте, как создавать экземпляры объектов

### <a name="instructions"></a>Инструкция

* В **проекта** панели, введите **ObjectSpawner** в поле поиска. Его также можно найти в разделе ресурсов/AppPrefabs /
* Перетащите **ObjectSpawner** prefab в **иерархии** панели.
* Нажмите кнопку **ObjectSpawner** в **иерархии** панели.
* **ObjectSpawner** есть поле с именем **цвет источника**.
* Из **иерархии** панели, перетащите **ColorPickerWheel** ссылку в это поле.

![Инспектор Spawner объектов](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* Нажмите кнопку **ObjectSpawner** prefab в **иерархии** панели.
* В **инспектор** панели, дважды щелкните **ObjectSpawner** скрипт, чтобы просмотреть код в Visual Studio.

**Сценарий ObjectSpawner**

**ObjectSpawner** создает копии примитив сетки (куб, sphere, цилиндра) в пространстве. Когда **InteractionSourcePressed** обнаруживается, он проверяет рабочей руки пользователя и если это **InteractionSourcePressType.Grasp** или **InteractionSourcePressType.Select** событие.

Для **осознавать** событие, он увеличивает индекс текущего типа сетки (сферу, куб, цилиндр)

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

Для **выберите** событий в **SpawnObject()**, новый объект, созданный экземпляр, без родительского элемента и освобожденных в мир.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner** использует **ColorPickerWheel** для задания цвета материала экранного объекта. Порожденный объектам предоставляется экземпляр этого материала, поэтому они сохранит их цвет.
* **Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки.

Можно изменять объекты с помощью кнопки коммерческих тайн и породить объектов с помощью кнопки "выбрать".

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Построение и развертывание приложения в смешанной реальности портала
* В Unity, выберите **файл > Параметры сборки**.
* Нажмите кнопку **добавьте откройте сцены** Добавление текущей сцены **построения кадром**.
* Щелкните **Сборка**.
* Создание **новую папку** с именем «Приложение».
* Одним щелчком мыши **приложения** папки.
* Щелкните элемент **Выбор папки**.
* По завершении Unity появится окно проводника.
* Откройте **приложения** папки.
* Дважды щелкните **YourSceneName.sln** файл решения Visual Studio.
* С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **X64**.
* Щелкните стрелку раскрывающегося списка рядом с кнопкой устройство и выберите **локальный компьютер**.
* Нажмите кнопку **Отладка -> Запуск без отладки** в меню или нажмите клавишу **Ctrl + F5**.

Теперь является построение и установке приложения на портале смешанной реальности. Его можно запустить снова через меню "Пуск" на портале смешанной реальности.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Дизайн — средства кисть с радиальным макета

![MixedReality213 Main](images/mr213-main-600px.jpg)

В этой главе вы узнаете, как заменить модель контроллера движения по умолчанию коллекция средство пользовательской кисти. Для справки можно найти завершенного сцены **MixedReality213Advanced** под **сцены** папки.

### <a name="instructions"></a>Инструкция

* В **проекта** панели, введите **BrushSelector** в поле поиска. Его также можно найти в разделе ресурсов/AppPrefabs /
* Перетащите **BrushSelector** prefab в **иерархии** панели.
* Для организации, создайте пустой объект GameObject вызывается **кисти**
* Перетащите следующие prefabs из **проекта** в область переноса **кисти**
    * Активы/AppPrefabs/**BrushFat**
    * Активы/AppPrefabs/**BrushThin**
    * Активы/AppPrefabs/**Ластик**
    * Активы/AppPrefabs/**MarkerFat**
    * Активы/AppPrefabs/**MarkerThin**
    * Активы/AppPrefabs/**карандаш**

![Кисти](images/mixedreality213-brushes-250px.png)
* Нажмите кнопку **MotionControllers** prefab в **иерархии** панели.
* В **инспектор** панели, снимите флажок **всегда использовать альтернативный справа модель** на **движения контроллера визуализатора**
* В **иерархии** панели, щелкните **BrushSelector**
* **BrushSelector** есть поле с именем **ColorPicker**
* Из **иерархии** панели, перетащите **ColorPickerWheel** в **ColorPicker** в **инспектор** панели.

![Назначить ColorPickerWheel для кисти выбора варианта](images/mr213-brushselector-500px.jpg)
* В **иерархии** панели **BrushSelector** prefab, выберите **меню** объекта.
* В **инспектор** панели **LineObjectCollection** компонента, откройте **объектов** раскрывающийся список массива. Вы увидите 6 пустых слотов.
* Из **иерархии** панели, перетащите prefabs, имеют родителей, в разделе **кисти** GameObject в эти слоты в любом порядке. (Убедитесь, что перетаскивания prefabs из сцены, не prefabs в папке проекта.)

![Селектор кисти](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefab**

Так как **BrushSelector** наследует **AttachToController**, он показывает **рабочей руки пользователя** и **элемент** параметры в  **Инспектор** панели. Мы выбрали **справа** и **указывает представлять** для присоединения кисть в правом нижнем контроллер в прямом направлении.

**BrushSelector** использует две служебные программы:
* **Эллипс**: используется для создания точек в пространстве по фигуре эллипса.
* **LineObjectCollection**: распределение объектов с помощью точки, созданные в любой строке класс (например, эллипс). Это, что мы будем использовать для размещения наших кисти вдоль фигуры Ellipse.

Вместе эти служебные программы можно использовать для создания радиального меню.

**Сценарий LineObjectCollection**

**LineObjectCollection** есть элементы управления для размера, положения и поворота объектов, распределенных по его линии. Это полезно для создания радиального меню как селектор кисти. Чтобы создать внешний вид кисти, масштабирования из nothing, так как они подходят положение выбранного центра обработки **ObjectScale** кривой пиковых нагрузок в центре и сходит по краям.

**Сценарий BrushSelector**

В случае использования **BrushSelector**, мы решили использовать процедурного анимации. Во-первых, кисть моделей распространяются в эллипс с **LineObjectCollection** скрипта. Затем каждый кисть несет ответственность за ведение его позиции в руки пользователя на основе его **DisplayMode** значение, которое изменяется в зависимости от выбора. Мы выбрали процедурном подходе из-за высокой вероятности переходов позиции кисти, выполняется прерывание пользователь выбирает кисти. Mecanim анимации могут правильно обработать перерывы в работе, но может быть сложнее, чем простой операции Lerp.

**BrushSelector** используется их сочетание. При обнаружении сенсорной панели ввода параметров кисти становятся видимыми и увеличить масштаб вдоль радиального меню. По истечении времени ожидания (который указывает, что пользователь сделал выбор) кисть параметров масштабирования вниз, оставляя только выбранной кисти.

**Визуализация ввода сенсорной панели**

Даже в случаях, когда модель контроллера был полностью заменен он может быть полезно показать ввода на исходные входные данные модели. Это помогает заземление действий пользователя, на самом деле. Для **BrushSelector** мы решили отобразить сенсорной панели кратко при получении входных данных. Это было сделано, получив элемент сенсорной панели из контроллера, заменив его материал пользовательского материала, а затем применение градиента этот материал цветов в зависимости от последнее время сенсорной ввод получен.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**Выбор инструментов кисти с входными данными для сенсорной панели**

Обнаружив селекторе кисть сенсорной панели в нажатом состоянии входных данных, он проверяет позицию ввода, чтобы определить, была ли она влево или вправо.

**Толщина штриха с selectPressedAmount**

Вместо **InteractionSourcePressType.Select** событие в **InteractionSourcePressed()**, можно получить аналогового значение нажатом величину посредством **selectPressedAmount**. Это значение можно получить в **InteractionSourceUpdated()**.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**Скрипт Ластик**

**Ластик** — это специальный тип кисть, которая переопределяет базовый **кисть** **DrawOverTime()** функции. Во время рисования имеет значение true, резинки проверяет, пересекается ли его tip с любой существующей мазков кисти. В этом случае они добавляются в очередь для работы и удалены.

## <a name="advanced-design---teleportation-and-locomotion"></a>Дополнительные возможности макета - Teleportation и locomotion

Если вы хотите разрешить пользователю перемещать сцены с помощью джойстик teleportation, используйте **MixedRealityCameraParent** вместо **MixedRealityCamera**. Необходимо также добавить **InputManager** и **DefaultCusor**. Так как **MixedRealityCameraParent** уже включает в себя **MotionControllers** и **границ** как дочерние компоненты, необходимо удалить существующий  **MotionControllers** и **среды** prefab.

### <a name="instructions"></a>Инструкция

* В **иерархии** панели, удалите **MixedRealityCamera**, **среды** и **MotionControllers**
* Из **панель проекта**, найдите и перетащите следующие prefabs в **иерархии** панели:
    * Активы/AppPrefabs/входныеданные/Prefabs/**MixedRealityCameraParent**
    * Активы/AppPrefabs/входныеданные/Prefabs/**InputManager**
    * Активы/AppPrefabs/входныеданные/Prefabs/курсор/**DefaultCursor**

![Родительский смешанной реальности камера](images/mr213-cameraparent-300px.png)
* В **иерархии** панели, щелкните **диспетчер ввода**
* В **инспектор** панели, прокрутите вниз до раздела **простой единичный выбор указатель** раздел
* Из **иерархии** панели, перетащите **DefaultCursor** в **курсор** поля

![Назначение DefaultCursor](images/mr213-defaultcursor-500px.png)
* **Сохранить** сцены и нажмите кнопку **воспроизведение** кнопки. Можно использовать джойстик для поворота влево/вправо или teleport.

## <a name="the-end"></a>Конец

И это, чтобы в конце этого руководства! Вы узнали:
* Как работать с моделями движения контроллер в режим игры и среды выполнения Unity.
* Сведения об использовании различных типов событий кнопки и их приложения.
* Как наложение элементов пользовательского интерфейса на основе контроллера или полностью настроить.

Теперь вы готовы приступить к созданию собственного присутствия с контроллерами движения!

## <a name="completed-scenes"></a>Завершенные сцены

* В Unity **проекта** щелкните панель **сцены** папки.
* Вы найдете два Unity sceens **MixedReality213** и **MixedReality213Advanced**.
    * **MixedReality213**: Завершенные сцены с помощью одной кисти
    * **MixedReality213Advanced**: Завершенные сцены с помощью нескольких кисти с примером сумма нажмите кнопки select

## <a name="see-also"></a>См. также

* [Файлы проекта 213 MR входных данных](https://github.com/Microsoft/MixedReality213)
* [Смешанной реальности Toolkit — сцены движения контроллера тестирования](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Набор средств для смешанной реальности - механизм захвата](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Рекомендации по разработке контроллера движения](motion-controllers.md)
