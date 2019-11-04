---
title: Ввод MR 213
description: Следуйте этому руководству по программированию с помощью Unity, Visual Studio и впечатляющих головных телефонов для получения сведений об контроллерах движения.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, иммерсивное, контроллер движения, Academy, руководство
ms.openlocfilehash: e2199c3afed21f9396ed84f71093a8b2fb3bb23b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438548"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Для HoloLens 2 опубликована [Новая серия руководств](mrlearning-base.md) .

<br>

# <a name="mr-input-213-motion-controllers"></a>Ввод с MR 213: контроллеры движения

Контроллеры движения в мире смешанной реальности добавляют еще один уровень интерактивности. Используя [контроллеры движения](motion-controllers.md), мы можем напрямую взаимодействовать с объектами более естественным образом, аналогично нашим физическим взаимодействиям в реальном времени, повышая иммерсивное и удовлетворения запросов в работе приложения.

В MR input 213 мы рассмотрим события ввода контроллера движения, создав простой интерфейс для пространственного рисования. С помощью этого приложения пользователи могут закрашивать трехмерное пространство с помощью различных типов кистей и цветов.

## <a name="topics-covered-in-this-tutorial"></a>Темы, описанные в этом руководстве

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Визуализация контроллера**|**События ввода контроллера**|**Пользовательский контроллер и пользовательский интерфейс**|
|Узнайте, как визуализировать модели контроллеров движения в игровом режиме и среде выполнения Unity.|Изучите различные типы событий кнопок и их приложений.|Узнайте, как наложение элементов пользовательского интерфейса поверх контроллера или его полная настройка.|

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td>Ввод с MR 213: контроллеры движения</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>Необходимые условия

См. Контрольный список установки для впечатляющих головных телефонов на [этой странице](install-the-tools.md).

* Для работы с этим руководством требуется [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Файлы проекта

* [Скачайте файлы](https://github.com/Microsoft/MixedReality213/archive/master.zip) , необходимые для проекта, и извлеките файлы на Рабочий стол.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Установка Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Задачи

* Оптимизация Unity для разработки Windows Mixed Reality
* Настройка камеры смешанной реальности
* Среда установки

### <a name="instructions"></a>Инструкция

* Запустите Unity.
* Нажмите кнопку **Открыть**.
* Перейдите к рабочему столу и найдите папку **MixedReality213-Master** , которая ранее была неархивирована.
* Щелкните элемент **Выбор папки**.
* После того как Unity закончит загрузку файлов проекта, вы сможете увидеть редактор Unity.
* В Unity выберите **файл > параметры сборки**.

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* Выберите **универсальная платформа Windows** в списке **платформа** и нажмите кнопку **переключателя платформы** .
* Задать целевое устройство для **любого устройства**
* Задать для типа сборки **D3D**
* Установить **последний установленный** пакет SDK
* Проверка **проектов C# Unity**
    * Это позволяет изменять файлы скриптов в проекте Visual Studio без перестроения проекта Unity.
* Щелкните **Параметры проигрывателя**.
* Прокрутите панель **инспектора** вниз до конца
* В параметрах XR проверьте, **поддерживается ли виртуальная реальность**
* В разделе пакеты SDK для Virtual Reality выберите **Windows Mixed Reality** .

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* Закройте окно **параметров сборки** .

### <a name="project-structure"></a>Структура проекта

В этом руководстве используется **[набор средств для смешанной реальности — Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** . Выпуски можно найти на [этой странице](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![прожектструктуре](images/mr213-projectstructure-650px.png)

**Завершенные монтажные кадры для справки**

* В папке **сцены** вы найдете два завершенных сцен Unity.
    * **MixedReality213**: завершено сцену с одной кистью
    * **MixedReality213Advanced**: Готовая сцена для расширенного проектирования с несколькими кистями

**Настройка новой сцены для учебника**

* В Unity щелкните **файл > создать сцену** .
* Удаление **основной камеры** и **направленного освещения**
* На **панели проект**найдите и перетащите следующий Prefabs на панель **Иерархия** :
    * Assets/Холотулкит/input/Prefabs/**микседреалитикамера**
    * Активы/Апппрефабс/**Среда**

    ![Камера и среда](images/mr213-cameraenvironment-300px.jpg)

* В наборе средств Mixed Reality есть два Prefabs камеры:
    * **Микседреалитикамера. prefab**: только Камера
    * **Микседреалитикамерапарент. prefab**: Камера + телеперенос + граница
    * В этом учебнике мы будем использовать **микседреалитикамера** без функции телепереноса. По этой причине мы добавили простой prefab **среды** , который содержит базовое основание для того, чтобы пользователь был заземлен.
    * Дополнительные сведения о сопоставлении с **микседреалитикамерапарент**см. в статье [Расширенный Дизайн — телесхема и локомотион](#advanced-design---teleportation-and-locomotion) .

**Установка скибокс**

* Щелкните **окно > освещение > параметры**
* Щелкните окружность справа от **поля Скибокс Material (материальный материал** ).
* Введите "серый" и выберите **скибоксграй** (Assets/Апппрефабс/support/Materials/скибоксграй. Asset).

    ![Настройка скибокс](images/mr123-skyboxsetting-400px.jpg)

* Проверьте параметр **скибокс** , чтобы увидеть назначенный серый градиент скибокс

    ![Переключить параметр скибокс](images/mr213-skyboxcheck-400px.jpg)

* Сцена с Микседреалитикамера, средой и серым скибокс будет выглядеть следующим образом.

    ![Среда MixedReality213](images/mr213-environment-600px.jpg)

* Щелкните **файл > сохранить сцену как** .
* **Сохраните** сцену в папке сцены с любым именем.

## <a name="chapter-1---controller-visualization"></a>Глава 1. Визуализация контроллера

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Задачи

* Узнайте, как визуализировать модели контроллеров движения в игровом режиме Unity и во время выполнения.

Windows Mixed Reality предоставляет анимированную модель контроллера для визуализации контроллера. Существует несколько подходов, которые можно предпринять для визуализации контроллера в приложении:

* По умолчанию — использование контроллера по умолчанию без изменения
* Гибридный — использование контроллера по умолчанию, но настройка некоторых его элементов или переверстка компонентов пользовательского интерфейса
* Замена. с помощью собственной настраиваемой трехмерной модели контроллера

В этой главе мы рассмотрим примеры этих настроек контроллера.

### <a name="instructions"></a>Инструкция

* На панели **проект** введите **мотионконтроллерс** в поле поиска. Его также можно найти в разделе Assets/Холотулкит/input/Prefabs/.
* Перетащите **мотионконтроллерс** prefab на панель **Иерархия** .
* Щелкните **мотионконтроллерс** prefab на панели **Иерархия** .

**Мотионконтроллерс prefab**

**Мотионконтроллерс** prefab содержит скрипт **мотионконтроллервисуализер** , который предоставляет слоты для альтернативных моделей контроллера. Если вы назначили собственные настраиваемые трехмерные модели, такие как рука или технологий, и установите флажок "всегда использовать альтернативную левую или правую модель", вы увидите их вместо модели по умолчанию. Мы будем использовать этот слот в главе 4 для замены модели контроллера на кисть.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Водим**

* На панели **инспектора** дважды щелкните сценарий **мотионконтроллервисуализер** , чтобы просмотреть код в Visual Studio.

**Сценарий Мотионконтроллервисуализер**

Классы **мотионконтроллервисуализер** и **мотионконтроллеринфо** предоставляют средства для доступа к & изменения моделей контроллеров по умолчанию. **Мотионконтроллервисуализер** подписывается на событие **интерактионсаурцедетектед** Unity и автоматически создает экземпляры моделей контроллеров при их обнаружении.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Модели контроллера доставляются в соответствии со [спецификацией глтф](https://github.com/KhronosGroup/glTF). Этот формат был создан для предоставления общего формата, в то же время улучшая процесс передачи и распаковки трехмерных ресурсов. В этом случае нам нужно извлечь и загрузить модели контроллера во время выполнения, так как мы хотим сделать работу пользователя максимально эффективной, а также не гарантируется, какая версия контроллеров движения может использоваться пользователем. В этом курсе с помощью набора средств Mixed Reality используется версия [проекта Унитиглтф](https://github.com/KhronosGroup/UnityGLTF)группы кхронос.

После доставки контроллера скрипты могут использовать **мотионконтроллеринфо** для поиска преобразований для конкретных элементов контроллера, чтобы они могли правильно позиционироваться.

В следующей главе будет показано, как использовать эти скрипты для присоединения элементов пользовательского интерфейса к контроллерам.

*В некоторых сценариях вы найдете блоки кода с **#if! UNITY_EDITOR** или **UNITY_WSA**. Эти блоки кода выполняются только в среде выполнения UWP при развертывании в Windows. Это обусловлено тем, что набор интерфейсов API, используемых редактором Unity и средой выполнения приложений UWP, отличается.*

* **Сохраните** сцену и нажмите кнопку **воспроизвести** .

Вы увидите сцену с контроллерами движения на гарнитуре. Можно просмотреть подробные анимации для нажатий кнопок, движения аналогового стика и выделения сенсорной панели.

![MR213_Controller визуализации по умолчанию](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Глава 2. присоединение элементов пользовательского интерфейса к контроллеру

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Задачи

* Сведения об элементах контроллеров Motion
* Сведения о присоединении объектов к конкретным частям контроллеров

В этой главе вы узнаете, как добавлять элементы пользовательского интерфейса к контроллеру, к которому пользователь может легко получать доступ и работать в любое время. Вы также узнаете, как добавить простой пользовательский интерфейс выбора цвета с помощью сенсорной панели ввода.

### <a name="instructions"></a>Инструкция

* На панели **проект** найдите скрипт **мотионконтроллеринфо** .
* В результатах поиска дважды щелкните **мотионконтроллеринфо** script, чтобы увидеть код в Visual Studio.

**Сценарий Мотионконтроллеринфо**

Первым шагом является выбор элемента контроллера, к которому должен быть присоединен пользовательский интерфейс. Эти элементы определяются в **контроллерелементенум** в **MotionControllerInfo.CS**.

![MR213 Мотионконтроллерелементс](images/mr213-motioncontrollerelements-1000px.jpg)

* **Домом**
* **Меню**
* **Осознавать**
* **Джойстик**
* **Метьте**
* **Сенсорная панель**
* **Указание** элемента "элемент" — Этот пункт представляет собой Совет контроллера, указывающего направление вперед.

**Водим**

* На панели **проект** найдите скрипт **аттачтоконтроллер** .
* В результатах поиска дважды щелкните **аттачтоконтроллер** script, чтобы увидеть код в Visual Studio.

**Сценарий Аттачтоконтроллер**

Скрипт **аттачтоконтроллер** предоставляет простой способ присоединения любых объектов к указанному контроллеру правой или левой и элементу.

В **аттачелементтоконтроллер ()** ,

* Проверьте правой или левой с помощью **мотионконтроллеринфо. правой или левой**
* Получение конкретного элемента контроллера с помощью **мотионконтроллеринфо. трижетелемент ()**
* После получения преобразования элемента из модели контроллера родительский объект наследуется от него и задается локальное расположение объекта, &ное вращение к нулю.

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

Самый простой способ использовать сценарий **аттачтоконтроллер** — это наследовать от него, как мы сделали в случае **колорпиккервхил.** Просто переопределите функции **онаттачтоконтроллер** и **ондетатчфромконтроллер** , чтобы выполнить настройку или декомпозицию при обнаружении или отключении контроллера.

**Водим**

* На панели **проект** введите в поле поиска **колорпиккервхил**. Его также можно найти в разделе Assets/Апппрефабс/.
* Перетащите **колорпиккервхил** prefab на панель **Иерархия** .
* Щелкните **колорпиккервхил** prefab на панели **Иерархия** .
* На панели **инспектора** дважды щелкните сценарий **колорпиккервхил** , чтобы просмотреть код в Visual Studio.

![Колорпиккервхил prefab](images/mr213-colorpickerwheel-1000px.jpg)

**Сценарий Колорпиккервхил**

Поскольку **колорпиккервхил** наследует **аттачтоконтроллер**, он отображает **правой или левой** и **элемент** на панели **инспектора** . Мы будем прикреплять пользовательский интерфейс к элементу сенсорной панели на левом контроллере.

![Сценарий Колорпиккервхил](images/mr213-attachtocontroller-300px.jpg)

**Колорпиккервхил** переопределяет **онаттачтоконтроллер** и **ондетатчфромконтроллер** для подписки на событие ввода, которое будет использоваться в следующей главе для выбора цвета с помощью ввода с сенсорной панели.

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

* **Сохраните** сцену и нажмите кнопку **воспроизвести** .

**Альтернативный способ присоединения объектов к контроллерам**

Рекомендуется, чтобы сценарии наследовались от **аттачтоконтроллер** и переопределяют **онаттачтоконтроллер**. Однако это не всегда возможно. Альтернативой является использование его в качестве отдельного компонента. Это может быть полезно, если необходимо подключить существующий prefab к контроллеру без рефакторинга скриптов. Просто попросите своего класса присвоить параметру Attach значение true, прежде чем выполнять настройку. Самый простой способ сделать это — использовать соподпрограмму для "Start."

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Глава 3. Работа с вводом сенсорной панели

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Задачи

* Узнайте, как получить события входных данных сенсорной панели
* Узнайте, как использовать сведения о положении оси сенсорной панели для работы с приложением

### <a name="instructions"></a>Инструкция

* На панели **Иерархия** щелкните **колорпиккервхил** .
* На панели **инспектора** в разделе **Аниматиор**дважды щелкните **колорпиккервхилконтроллер** .
* Вы сможете увидеть открытую вкладку **аниматор**

**Отображение или скрытие пользовательского интерфейса с помощью контроллера анимации Unity**

Чтобы показать или скрыть пользовательский интерфейс **колорпиккервхил** с анимацией, мы используем [систему анимации Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Установка значения true или false для свойства **Visible** объекта **колорпиккервхил**позволяет **Отображать** и **скрывать** триггеры анимации. Параметры **отображения** и **скрытия** определяются в контроллере анимации **колорпиккервхилконтроллер** .

![Контроллер анимации Unity](images/mr123-animationcontroller-550px.jpg)

**Водим**

* На панели **Иерархия** выберите **колорпиккервхил** prefab.
* На панели **инспектора** дважды щелкните сценарий **колорпиккервхил** , чтобы просмотреть код в Visual Studio.

**Сценарий Колорпиккервхил**

**Колорпиккервхил** подписывается на событие **интерактионсаурцеупдатед** Unity для прослушивания событий сенсорной панели.

В **интерактионсаурцеупдатед ()** сценарий сначала проверяет, чтобы убедиться, что он:

* фактически является событием сенсорной панели (obj. State. **Таучпадтаучед**)
* исходит от левого контроллера (obj. State. Source. **правой или левой**)

Если оба значения имеют значение true, расположение сенсорной панели (obj. State. **Таучпадпоситион**) назначается **селекторпоситион**.

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

В **Update ()** , основанном на **видимом** свойстве, он запускает отображение и скрытие триггеров анимации в компоненте аниматор средства выбора цвета.

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

В **Update ()** **селекторпоситион** используется для приведения луча по отношению к конфликту сетчатого цветового круга, который возвращает UV-расположение. Эта положение затем можно использовать для поиска координат пиксела и цвета текстуры цветового круга. Это значение доступно для других скриптов через свойство **селектедколор** .

![Палитра выбора цвета колесо Райкастинг](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a>Глава 4. Переопределение модели контроллера

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Задачи

* Узнайте, как переопределить модель контроллера с помощью настраиваемой трехмерной модели.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Инструкция

* На панели **Иерархия** щелкните **мотионконтроллерс** .
* Щелкните окружность справа от поля **альтернативный контроллер справа** .
* Введите **"брушконтроллер**" и выберите prefab из результата. Его можно найти в разделе Assets/Апппрефабс/**брушконтроллер**.
* Проверка **всегда использовать другую правильную модель**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

**Брушконтроллер** prefab не обязательно включать в панель **Иерархия** . Однако, чтобы извлечь его дочерние компоненты:

* На панели **проект** введите **Брушконтроллер** и перетащите **брушконтроллер** prefab на панель **Иерархия** .

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Вы найдете компонент **Tip** в **брушконтроллер**. Мы будем использовать его преобразование для запуска и завершения рисования линий.

* Удалите **брушконтроллер** с панели **Иерархия** .
* **Сохраните** сцену и нажмите кнопку **воспроизвести** . Вы сможете увидеть, что модель кистей заменила правый контроллер движения.

## <a name="chapter-5---painting-with-select-input"></a>Глава 5. Рисование с помощью выбора входных данных

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Задачи

* Узнайте, как использовать событие кнопки "выбрать" для запуска и завершения рисования линий

### <a name="instructions"></a>Инструкция

* Выполните поиск по запросу **брушконтроллер** prefab на панели **проекта** .
* На панели **инспектора** дважды щелкните сценарий **брушконтроллер** , чтобы просмотреть код в Visual Studio.

**Сценарий Брушконтроллер**

**Брушконтроллер** подписывается на события **Интерактионсаурцепрессед** и **интерактионсаурцерелеасед** интерактионманажер. При запуске события **интерактионсаурцепрессед** свойство **Draw** кисти устанавливается в значение true. При запуске события **интерактионсаурцерелеасед** свойство **Draw** кисти устанавливается в значение false.

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

Если параметр **Draw** имеет значение true, кисть создаст точки в экземпляре Unity **линерендерер**. Ссылка на этот prefab хранится в поле **Stroke prefab** кисти.

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

Чтобы использовать текущий выбранный цвет в пользовательском интерфейсе колесика выбора цвета, **брушконтроллер** должен иметь ссылку на объект **колорпиккервхил** . Так как экземпляр **брушконтроллер** prefab создается во время выполнения в качестве контроллера замены, все ссылки на объекты в сцене должны быть заданы во время выполнения. В этом случае мы используем **GameObject. финдобжектофтипе** для размещения **колорпиккервхил**:

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

* **Сохраните** сцену и нажмите кнопку **воспроизвести** . Вы сможете рисовать линии и рисовать с помощью кнопки выбрать в правом контроллере.

## <a name="chapter-6---object-spawning-with-select-input"></a>Глава 6 — порождение объекта с помощью выбора входных данных

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Задачи

* Узнайте, как использовать кнопки выбора и изучения событий ввода
* Узнайте, как создавать экземпляры объектов

### <a name="instructions"></a>Инструкция

* На панели **проект** введите **обжектспавнер** в поле поиска. Его также можно найти в разделе Assets/Апппрефабс/
* Перетащите **обжектспавнер** prefab на панель **Иерархия** .
* На панели **Иерархия** щелкните **обжектспавнер** .
* **Обжектспавнер** имеет поле с именем **источник цвета**.
* На панели **Иерархия** перетащите ссылку **колорпиккервхил** в это поле.

    ![Инспектор порождаемых объектов](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* Щелкните **обжектспавнер** prefab на панели **Иерархия** .
* На панели **инспектора** дважды щелкните сценарий **обжектспавнер** , чтобы просмотреть код в Visual Studio.

**Сценарий Обжектспавнер**

**Обжектспавнер** создает в пространстве экземпляры копий примитивной сетки (куб, шар, цилиндр). При обнаружении **интерактионсаурцепрессед** проверяет правой или левой и, если это событие **интерактионсаурцепресстипе.** поняли или **интерактионсаурцепресстипе. Select** .

Для события с учетом **усвоения** он увеличивает индекс текущего типа сетки (шар, куб, цилиндр).

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

Для события **SELECT** в **спавнобжект ()** создается экземпляр нового объекта, не являющийся родительским и освобожденный в мире.

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

**Обжектспавнер** использует **колорпиккервхил** для установки цвета материала экранного объекта. Порожденным объектам присваивается экземпляр этого материала, чтобы они сохраняли свой цвет.

* **Сохраните** сцену и нажмите кнопку **воспроизвести** .

Вы сможете изменить объекты с помощью кнопки "располагаться" и порождением объектов с помощью кнопки "выбрать".

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Создание и развертывание приложения на портале смешанной реальности

* В Unity выберите **файл > параметры сборки**.
* Нажмите кнопку **Добавить открытые сцены** , чтобы добавить текущую сцену в **сцена в сборке**.
* Щелкните **Сборка**.
* Создайте **новую папку** с именем App.
* Щелкните папку **приложения** одним щелчком мыши.
* Щелкните элемент **Выбор папки**.
* После завершения Unity появится окно проводника.
* Откройте папку **приложения** .
* Дважды щелкните файл решения Visual Studio **йоурсцененаме. sln** .
* С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x64**.
* Щелкните стрелку раскрывающегося списка рядом с кнопкой устройство и выберите **локальный компьютер**.
* Щелкните **Отладка-> запуск без отладки** в меню или нажмите клавиши **CTRL + F5**.

Теперь приложение создается и устанавливается на портале смешанной реальности. Вы можете запустить его снова через меню "Пуск" на портале Mixed Reality.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Дополнительные инструменты проектирования и кисти с радиальным макетом

![MixedReality213 Main](images/mr213-main-600px.jpg)

В этой главе вы узнаете, как заменить модель контроллера движения по умолчанию на коллекцию настраиваемых инструментов кисти. Для справки можно найти завершенную сцену **MixedReality213Advanced** в папке **сцены** .

### <a name="instructions"></a>Инструкция

* На панели **проект** введите **брушселектор** в поле поиска. Его также можно найти в разделе Assets/Апппрефабс/
* Перетащите **брушселектор** prefab на панель **Иерархия** .
* Для организации создайте пустой GameObject с именем **кисти** .
* Перетащите следующие Prefabs с панели **проект** на **кисти** .
    * Активы/Апппрефабс/**брушфат**
    * Активы/Апппрефабс/**брушсин**
    * Активы/Апппрефабс/**резинка**
    * Активы/Апппрефабс/**маркерфат**
    * Активы/Апппрефабс/**маркерсин**
    * Активы/Апппрефабс/**карандаш**

    ![Кисти](images/mixedreality213-brushes-250px.png)

* Щелкните **мотионконтроллерс** prefab на панели **Иерархия** .
* На панели **инспектора** снимите флажок **всегда использовать другую правильную модель** на **визуализаторе контроллера движения** .
* На панели **Иерархия** щелкните **брушселектор** .
* **Брушселектор** содержит поле с именем **ColorPicker** .
* На панели « **Иерархия** » перетащите поле **колорпиккервхил** в **ColorPicker** на панели **инспектора** .

    ![Назначение Колорпиккервхил селектору кисти](images/mr213-brushselector-500px.jpg)

* На панели **Иерархия** в разделе **брушселектор** prefab выберите объект **меню** .
* На панели **инспектора** в разделе компонент **линеобжектколлектион** откройте раскрывающийся список массив **объектов** . Вы увидите 6 пустых слотов.
* На панели **Иерархия** перетащите все Prefabs, наявляющиеся от **кистей** , GameObject в эти слоты в любом порядке. (Убедитесь, что вы перетаскивайте Prefabs из сцены, а не из Prefabs в папке проекта.)

![Селектор кисти](images/mr213-brushselectorbrushes-700px.jpg)

**Брушселектор prefab**

Поскольку **брушселектор** наследует **аттачтоконтроллер**, он отображает параметры **правой или левой** и **element** на панели **инспектора** . Мы выбрали **право** и назначите элемент «рука **», чтобы** присоединить средства кистей к правому контроллеру с прямым направлением.

**Брушселектор** использует две служебные программы:

* **Эллипс**: используется для создания точек в пространстве вдоль фигуры эллипса.
* **Линеобжектколлектион**: распределяет объекты с помощью точек, созданных любым классом линии (например, эллипсом). Именно так мы будем использовать для размещения наших кистей вдоль эллипса.

В сочетании эти служебные программы можно использовать для создания радиального меню.

**Сценарий Линеобжектколлектион**

**Линеобжектколлектион** имеет элементы управления размером, расположением и поворотом объектов, распределенных вдоль линии. Это полезно для создания радиальных меню, таких как селектор кисти. Чтобы создать внешний вид кистей, которые не масштабируются по мере приближения к центру выбранной позиции, **обжектскале** кривая в центре и конусы на краях.

**Сценарий Брушселектор**

В случае с **брушселектор**мы решили использовать метод анимации. Во первых, модели кистей распределяются на эллипсе с помощью скрипта **линеобжектколлектион** . Затем каждая кисть несет ответственность за поддержание своего расположения в руки пользователя на основе его значения **DisplayMode** , которое изменяется в зависимости от выбора. Мы выбрали подход к методу из-за того, что высокая вероятность того, что переходы по положению кисти прерываются, так как пользователь выбирает кисти. Анимация меканим может правильно обрабатывать прерывания, но она, как правило, сложнее, чем простая операция Лерп.

**Брушселектор** использует сочетание обоих типов. При обнаружении ввода сенсорной панели Параметры кисти становятся видимыми и масштабируются вдоль радиального меню. По истечении времени ожидания (которое указывает, что пользователь сделал выбор) параметры кисти снова масштабируются, при этом остается только выбранная кисть.

**Визуализация ввода сенсорной панели**

Даже в тех случаях, когда модель контроллера была полностью заменена, может быть полезно отобразить входные данные исходной модели. Это позволяет заземление действий пользователя в реальности. Для **брушселектор** мы решили, чтобы сенсорная панель ненадолго отображалась при получении входных данных. Это было сделано путем извлечения элемента сенсорной панели из контроллера, замены его материала на пользовательский материал, а затем применения градиента к цвету материала на основе последнего полученного ввода сенсорной панели.

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

**Выбор инструмента "кисть" с входными данными сенсорной панели**

Когда селектор кисти обнаруживает нажатую клавишу сенсорного ввода, он проверяет расположение входных данных, чтобы определить, было ли оно равно левому или правому.

**Толщина штриха с помощью Селектпресседамаунт**

Вместо события **интерактионсаурцепресстипе. Select** в **интерактионсаурцепрессед ()** можно получить значение аналогового значения выделенной суммы через **селектпресседамаунт**. Это значение можно получить в **интерактионсаурцеупдатед ()** .

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

**Сценарий ластика**

**Ластик** — это специальный тип кисти, переопределяющий функцию **дравовертиме ()** базовой **кисти**. Когда Draw имеет значение true, резинка проверяет, пересекается ли его Совет с любыми существующими мазками кистью. Если это так, они добавляются в очередь для уменьшения и удаления.

## <a name="advanced-design---teleportation-and-locomotion"></a>Расширенный дизайн — локальная и локомотион

Если вы хотите разрешить пользователю перемещаться по сцене с помощью многопортового стика, используйте **микседреалитикамерапарент** вместо **микседреалитикамера**. Также необходимо добавить **InputManager** и **дефаулткусор**. Так **как микседреалитикамерапарент** уже включает **мотионконтроллерс** и **границу** как дочерние компоненты, следует удалить существующие prefab **мотионконтроллерс** и **среды** .

### <a name="instructions"></a>Инструкция

* На панели **Иерархия** удалите **микседреалитикамера**, **Environment** и **мотионконтроллерс** .
* На **панели проект**найдите и перетащите следующий Prefabs на панель **Иерархия** :
    * Assets/Апппрефабс/input/Prefabs/**микседреалитикамерапарент**
    * Assets/Апппрефабс/input/Prefabs/**InputManager**
    * Assets/Апппрефабс/input/Prefabs/Cursor/**дефаулткурсор**

    ![Родитель камеры смешанной реальности](images/mr213-cameraparent-300px.png)

* На панели **Иерархия** щелкните **Диспетчер входов** .
* На панели **инспектора** прокрутите вниз до раздела **простой единичный селектор указателя** .
* На панели **Иерархия** перетащите **дефаулткурсор** INTO в поле **курсора** .

    ![Назначение Дефаулткурсор](images/mr213-defaultcursor-500px.png)

* **Сохраните** сцену и нажмите кнопку **воспроизвести** . Вы сможете использовать аналоговый стик для поворота влево, вправо или телепортироваться.

## <a name="the-end"></a>Конец

И это окончание этого руководства. Вы узнали:

* Как работать с моделями контроллера движения в игровом режиме Unity и в среде выполнения.
* Использование различных типов событий кнопок и их приложений.
* Как наложение элементов пользовательского интерфейса поверх контроллера или его полная настройка.

Теперь вы готовы приступить к созданию своего собственного иммерсивного интерфейса с помощью контроллеров движения!

## <a name="completed-scenes"></a>Завершенные сцены

* На панели **проекта** Unity щелкните папку " **сцены** ".
* Вы обнаружите два сцеенсов Unity и **MixedReality213** и **MixedReality213Advanced**.
    * **MixedReality213**: завершено сцену с одной кистью
    * **MixedReality213Advanced**: завершенная сцена с несколькими кистями с примером суммы нажатия кнопки SELECT

## <a name="see-also"></a>См. также

* [Файлы проекта с вводом в MR 213](https://github.com/Microsoft/MixedReality213)
* [Набор средств для смешанной реальности — тестовая сцена контроллера движения](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Набор средств для смешанной реальности — механики захвата](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Рекомендации по разработке для контроллера движения](motion-controllers.md)
