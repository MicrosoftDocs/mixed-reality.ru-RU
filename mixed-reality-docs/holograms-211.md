---
title: Входные данные MR 211 - жестов
description: Выполнения данного кода пошагового руководства, с помощью Unity, Visual Studio и HoloLens Дополнительные сведения о концепции жест.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, учебник, жестов
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603384"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

# <a name="mr-input-211-gesture"></a>Входные данные MR 211: Жест

[Жесты](gestures.md) превратить намерение пользователя в действия. С помощью жестов пользователи могут взаимодействовать с голограммы. В рамках этого курса вы узнаете как отслеживать руки пользователя, реагировать на ввод данных пользователем и отзывов для пользователя зависимости в наличии, состоянии и расположении.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

В [101 основы MR](holograms-101.md), мы использовали жеста простой air касания для взаимодействия с нашей голограммы. Теперь мы за жест жест касания и изучение новых концепций, чтобы:

* Обнаружить при наличии пользователя отслеживается и обеспечивают отзыв для пользователя.
* Для изменения наш голограммы выполните жест навигации.
* Оставить отзыв, при наличии пользователя выходят за пределы представления.
* Позволяет разрешить пользователям перемещать голограммы разработчикам события манипуляции.

В этом курсе мы вернемся к проекта Unity **обозревателя моделей**, который мы создали [210 ввода MR](holograms-210.md). Наши friend-космонавты, годится возвращается в том, чтобы помочь нам в наши исследования этих новых концепций жест.

>[!IMPORTANT]
>Видео, внедренных в каждой главы ниже были записаны с использованием более старой версии Unity и смешанной реальности Toolkit. Хотя пошаговые инструкции и точной и актуальной, может появиться скрипты и визуальные элементы в соответствующих видео, становятся недействительными. Видеоролики остаются включены перемешаны и поскольку рассматриваются основные понятия по-прежнему применяются.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td>Входные данные MR 211: Жест</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>предварительные требования

* ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).
* Основные C# возможности программирования.
* Необходимо завершить [101 основы MR](holograms-101.md).
* Необходимо завершить [210 ввода MR](holograms-210.md).
* Устройство HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) требуемые для проекта. Требуется компонент Unity 2017.2 или более поздней версии.
* Удаление архива файлы рабочего стола или других легко положения.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Список ошибок и примечания

* «Включить только мой код» необходимо отключить (*unchecked*) в Visual Studio в разделе Сервис -> Параметры -> Отладка для точки останова в коде.

## <a name="chapter-0---unity-setup"></a>Глава 0 — Установка Unity

### <a name="instructions"></a>Инструкция

1. Запустите Unity.
2. Выберите **откройте**.
3. Перейдите к **жест** папку вы ранее не архивные.
4. Найдите и выберите **запуск**/**обозревателя моделей** папки.
5. Нажмите кнопку **Выбор папки** кнопки.
6. В **проекта** панели, разверните узел **сцены** папки.
7. Дважды щелкните **ModelExplorer** сцены, чтобы загрузить его в Unity.

### <a name="building"></a>Сборка

1. В Unity, выберите **файл > Параметры сборки**.
2. Если **сцены/ModelExplorer** не указан в **построения кадром**, нажмите кнопку **добавьте откройте сцены** Добавление сцены.
3. Если вы разрабатываете специально для HoloLens, задайте **целевое устройство** для **HoloLens**. В противном случае оставьте его на **любого устройства**.
4. Убедитесь, **построение** присваивается **D3D** и **SDK** имеет значение **самую новую установленную** (которое должно быть SDK 16299 или более поздней версии).
5. Щелкните **Сборка**.
6. Создание **новую папку** с именем «Приложение».
7. Одним щелчком мыши **приложения** папки.
8. Нажмите клавишу **Выбор папки** и Unity начнется построение проекта для Visual Studio.

По завершении Unity появится окно проводника.

1. Откройте **приложения** папки.
2. Откройте **решение ModelExplorer в Visual Studio**.

Если развертывание HoloLens:

1. С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x86**.
2. Щелкните стрелку раскрывающегося списка рядом с кнопкой на локальном компьютере и выберите **удаленный компьютер**.
3. Введите **IP-адрес устройства HoloLens** и задайте режим проверки подлинности **универсальный (незашифрованный протокол)**. Нажмите кнопку **выберите**. Если вы не знаете IP-адрес устройства, найдите в **параметры > сеть и Интернет > Дополнительно**.
4. В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**. Если это при первом развертывании к устройству, необходимо будет [свяжите его с помощью Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Когда приложение будет развернуто, закрыть **Fitbox** с **выберите жест**.

Если развертывание иммерсивных гарнитура:

1. С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **x64**.
2. Убедитесь, что целевой объект развертывания присваивается **локальный компьютер**.
3. В верхней строке меню, щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.
4. Когда приложение будет развернуто, закрыть **Fitbox** , потянув триггер на контроллере движения.

>[!NOTE]
>Вы можете заметить некоторые ошибки красным на панели ошибок Visual Studio. Можно безопасно пропускать их. Переключиться на панели «Вывод», чтобы просмотреть фактический ход выполнения сборки. Ошибки в панели «Вывод» потребуется внести исправление (наиболее часто они являются вызвана неправильным действием в скрипте).

## <a name="chapter-1---hand-detected-feedback"></a>Глава 1 - руки обнаружил обратной связи

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Цели

* Подписка для передачи событий отслеживания.
* Использование курсоров отображаются пользователи, при наличии отслеживается.

### <a name="instructions"></a>Инструкция

* В **иерархии** панели, разверните узел **InputManager** объекта.
* Найдите и выберите **GesturesInput** объекта.

**InteractionInputSource.cs** скрипт выполняет следующие действия:

1. Подписывается на события InteractionSourceDetected и InteractionSourceLost.
2. Задает состояние HandDetected.
3. Отменяет подписку на события InteractionSourceDetected и InteractionSourceLost.

Далее мы выполним обновление наших курсора из [210 ввода MR](holograms-210.md) в один из них обратной связи в зависимости от действий пользователя.

1. В **иерархии** панели, выберите **курсор** объекта и удалите его.
2. В **проекта** панели, поиск **CursorWithFeedback** и перетащите его в **иерархии** панели.
3. Щелкните **InputManager** в **иерархии** панели, а затем перетащите **CursorWithFeedback** объекта из **иерархии** в В InputManager **SimpleSinglePointerSelector** **курсор** поле в нижней части **инспектор**.
4. Щелкните **CursorWithFeedback** в **иерархии**.
5. В **инспектор** панели, разверните узел **данные о состоянии курсора** на **объект курсора** скрипта.

**Данные о состоянии курсора** работает следующим образом:

* Любой **наблюдения** состояние означает, что обнаружен не вручную пользователь просто всматриваться.
* Любой **взаимодействие** состояние означает, что Рука или контроллер обнаружил.
* Любой **при наведении указателя мыши** состояние означает, что пользователь просматривает голограмма.

### <a name="build-and-deploy"></a>Создание и развертывание

* В Unity, использовать **файл > Параметры сборки** для перестроения приложения.
* Откройте **приложения** папки.
* Если он не открыт, откройте **решение Visual Studio ModelExplorer**.
  * (Если вы уже сборки и развертывания этого проекта в Visual Studio во время установки, затем можно открыть этот экземпляр VS и нажмите кнопку «Обновить все» при появлении запроса).
* В Visual Studio щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.
* После развертывания приложения для HoloLens, закройте fitbox, с помощью жестов жест касания.
* Переместите свои силы в представлении и укажите палец неба, чтобы начать отслеживание вручную.
* Переместить свои силы влево, вправо, вверх и вниз.
* Посмотрите, как изменится курсор, после обнаружения и затем потеряна из представления свои силы.
* Если вы используете иммерсивных гарнитура, придется подключаться и отключаться от вашего контроллера. Ваши отзывы становится менее интересными на устройстве иммерсивных как подключенного контроллера всегда будет «доступно».

## <a name="chapter-2---navigation"></a>Глава 2 - навигации

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Цели

* Для изменения космонавты выполните жест событий навигации.

### <a name="instructions"></a>Инструкция

Чтобы использовать жесты для навигации в наше приложение, мы собираемся изменить **GestureAction.cs** поворачивают объекты, когда происходит жест навигации. Кроме того мы добавим отзыв курсор, отображаемый при навигации.

1. В **иерархии** панели, разверните узел **CursorWithFeedback**.
2. В **голограммы** папки, найти **ScrollFeedback** активов.
3. Перетаскивание **ScrollFeedback** prefab на **CursorWithFeedback** GameObject в **иерархии**.
4. Щелкните **CursorWithFeedback**.
5. В **инспектор** панели, щелкните **добавить компонент** кнопки.
6. В меню, введите в поле поиска **CursorFeedback**. Выберите результат поиска.
7. Перетаскивание **ScrollFeedback** объекта из **иерархии** на **прокрутки обнаружил игровой объект** свойство в **курсоров**компонент в **инспектор**.
8. В **иерархии** панели, выберите **AstroMan** объекта.
9. В **инспектор** панели, щелкните **добавить компонент** кнопки.
10. В меню, введите в поле поиска **действие жеста**. Выберите результат поиска.

Затем откройте **GestureAction.cs** в Visual Studio. При кодировании Упражнение 2.c, измените сценарий, выполнив следующие действия:

1. **Поворот AstroMan** при каждом выполнении жеста навигации.
2. Вычислить **rotationFactor** для управления угол поворота, применяются к объекту.
3. **Повернуть объект** вокруг оси y, когда пользователь перемещает их наличии влево или вправо.

Полный кода выполняет 2.c в скрипте или замените код готового решения ниже:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

Вы заметите, что другие события навигации уже заполнены некоторые сведения. Мы отправляем GameObject на набора средств в InputSystem модальное стека, так что пользователю не нужно Сконцентрируйтесь на космонавты, после начала поворота. Соответственно мы pop GameObject из стека, после завершения жест.

### <a name="build-and-deploy"></a>Создание и развертывание

1. Перестройте приложение в Unity, построение и развертывание из Visual Studio для запуска в HoloLens.
2. Помощи в космонавты, две стрелки должен появляться в разные стороны от курсора. Этот новый визуальный элемент указывает, что могут быть повернуты-космонавты, годится.
3. Поместить свои силы в готовности место (вытянутым указательным пальцем направлена sky), начнется HoloLens, отслеживания свои силы.
4. Чтобы повернуть космонавты, снизить палец в позицию жестом сжатия и переместите свои силы влево или вправо, чтобы активировать NavigationX жест.

## <a name="chapter-3---hand-guidance"></a>Глава 3 - инструкции вручную

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Цели

* Используйте **вручную Оценка рекомендации** для прогнозирования, при наличии отслеживания будут потеряны.
* Укажите **отзывы о курсор** для отображения, при наличии пользователя истекает камеры края представления.

### <a name="instructions"></a>Инструкция

1. В **иерархии** панели, выберите **CursorWithFeedback** объекта.
2. В **инспектор** панели, щелкните **добавить компонент** кнопки.
3. В меню, введите в поле поиска **наличии рекомендации**. Выберите результат поиска.
4. В **проекта** панели **голограммы** папки, найти **HandGuidanceFeedback** активов.
5. Перетаскивание **HandGuidanceFeedback** активов на **наличии рекомендации индикатор** свойства в **инспектор** панели.

### <a name="build-and-deploy"></a>Создание и развертывание

* Перестройте приложение в Unity, построение и развертывание из Visual Studio, чтобы оценить приложение в HoloLens.
* Видимым вашей руке и вызывать палец для отслеживания.
* Запустить смену-космонавты, годится с жестом навигации (сжатие палец и бегунок друг с другом).
* Переместите свои силы далеко влево, вправо, вверх и вниз.
* Как свои силы незадолго до края рамки жестов, рядом с полем появится стрелка курсора, предупреждающее о том, что Рука отслеживания будут потеряны. Стрелка указывает направление, в котором для перемещения свои силы во избежание отслеживания Предотвращение потери.

## <a name="chapter-4---manipulation"></a>Глава 4 – манипуляции

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Цели

* Позволяет переносить-космонавты, годится с рук события манипуляции.
* Оставить отзыв о курсор, чтобы позволить пользователю узнать, когда манипуляция может использоваться.

### <a name="instructions"></a>Инструкция

GestureManager.cs и AstronautManager.cs позволит нам сделайте следующее:

1. Используйте ключевое слово речи "**переместить космонавты**" для включения **манипуляции** жестов и "**повернуть космонавты**" отключить их.
2. Переключиться в режим реагирование на них **распознаватель жестов манипуляции**.

Начнем.

1. В **иерархии** панели, создать новый пустой объект GameObject. Назовите его "**AstronautManager**«.
2. В **инспектор** панели, щелкните **добавить компонент** кнопки.
3. В меню, введите в поле поиска **-космонавты, годится Manager**. Выберите результат поиска.
4. В **инспектор** панели, щелкните **добавить компонент** кнопки.
5. В меню, введите в поле поиска **источника ввода речи**. Выберите результат поиска.

Теперь мы добавим команды речи, необходимые для управления взаимодействия состоянием-космонавты, годится.

1. Разверните **ключевые слова** статьи **инспектор**.
2. Нажмите кнопку **+** на стороне справа, чтобы добавить новое ключевое слово.
3. Введите ключевое слово как **переместить космонавты**. Вы можете добавить ярлык ключ, при необходимости.
4. Нажмите кнопку **+** на стороне справа, чтобы добавить новое ключевое слово.
5. Введите ключевое слово как **повернуть космонавты**. Вы можете добавить ярлык ключ, при необходимости.
6. Соответствующий код обработчика можно найти в **GestureAction.cs**в **ISpeechHandler.OnSpeechKeywordRecognized** обработчика.

![Как настройки источника входных данных речи для главы 4](images/holograms211-speech.png)

Далее мы будем Настройка отзыв манипуляции над курсором.

1. В **проекта** панели **голограммы** папки, найти **PathingFeedback** активов.
2. Перетаскивание **PathingFeedback** prefab на **CursorWithFeedback** объекта в **иерархии**.
3. В **иерархии** панели, щелкнув **CursorWithFeedback**.
4. Перетаскивание **PathingFeedback** объекта из **иерархии** на **путь обнаружил игровой объект** свойство в **курсоров**компонент в **инспектор**.

Теперь нам нужно добавить код, чтобы **GestureAction.cs** возможным следующее:

1. Добавьте код для **IManipulationHandler.OnManipulationUpdated** функцию, которая будет переместить космонавты при **манипуляции** обнаружении жеста.
2. Вычислить **вектор перемещения** для определения, где следует перемещать космонавты, в основе стороны позиции.
3. **Переместить** -космонавты, годится на новое место.

Полный кодирования Упражнение 4.a в **GestureAction.cs**, или используйте наши готового решения ниже:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>Создание и развертывание

* Перестроить в Unity, построение и развертывание из Visual Studio, чтобы запустить приложение в HoloLens.
* Переместите свои силы перед HoloLens и вызывать палец, что его можно отслеживать.
* Сосредоточиться курсор над-космонавты, годится.
* Предположим, «Переместить космонавты», чтобы переместить-космонавты, годится с жестом манипуляции.
* Четыре стрелки появится этого курсора, чтобы указать, что программа теперь будут отвечать на события манипуляции.
* Уменьшите палец вниз, чтобы ваши бегунка и остаться pinched друг с другом.
* При перемещении вашей руке вокруг космонавты переместит слишком (это манипуляции).
* Вызывать палец для остановки обработки-космонавты, годится.
* Примечание. Если вы не ответите «Переместить космонавты» перед перемещением вашей руке, то жест навигации будет использоваться вместо этого.
* Произнесите «Поворот космонавты», чтобы вернуть Поворотный состояние.

## <a name="chapter-5---model-expansion"></a>Глава 5 - расширение модели

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Цели

* Разверните модели-космонавты, годится на несколько, более мелкие части, что пользователь может взаимодействовать с.
* Переместите каждый фрагмент, по отдельности с помощью жестов перехода и обработки.

### <a name="instructions"></a>Инструкция

В этом разделе мы предстоит выполнить следующие задачи:

1. Добавить новое ключевое слово "**разверните модель**" для расширения модели-космонавты, годится.
2. Добавить новое ключевое слово "**сброса модели**" для возвращения модели в своем первоначальном виде.

Мы будем сделать, добавив два дополнительных ключевых слова источника входных данных преобразования речи в предыдущей главе. Мы также покажем еще один способ обработки события распознавания.

1. Снова щелкните **AstronautManager** в **инспектор** и разверните **ключевые слова** статьи **инспектор**.
2. Нажмите кнопку **+** на стороне справа, чтобы добавить новое ключевое слово.
3. Введите ключевое слово как **расширяют модель**. Вы можете добавить ярлык ключ, при необходимости.
4. Нажмите кнопку **+** на стороне справа, чтобы добавить новое ключевое слово.
5. Введите ключевое слово как **сброса модели**. Вы можете добавить ярлык ключ, при необходимости.
6. В **инспектор** панели, щелкните **добавить компонент** кнопки.
7. В меню, введите в поле поиска **обработчика ввода речи**. Выберите результат поиска.
8. Проверьте **является глобальной прослушивателя**, поскольку необходимо, чтобы эти команды заработали независимо от того, GameObject мы сосредоточили.
9. Нажмите кнопку **+** и выберите **разверните модель** из раскрывающегося списка ключевое слово.
10. Нажмите кнопку **+** ответа и перетащите **AstronautManager** из **иерархии** в **None (объект)** поле.
11. Теперь щелкните **функции нет** раскрывающемся списке выберите **AstronautManager**, затем **ExpandModelCommand**.
12. Нажмите кнопку обработчика ввода речи **+** и выберите **сброса модели** из раскрывающегося списка ключевое слово.
13. Нажмите кнопку **+** ответа и перетащите **AstronautManager** из **иерархии** в **None (объект)** поле.
14. Теперь щелкните **функции нет** раскрывающемся списке выберите **AstronautManager**, затем **ResetModelCommand**.

![Как настроить источник ввода речи и обработчик для главы 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Создание и развертывание

* Попробуйте! Создавайте и развертывайте приложения для HoloLens.
* Скажем **разверните модель** для космонавты развернутой модели см. в разделе.
* Используйте **навигации** для поворота отдельные части масти-космонавты, годится.
* Скажем **переместить космонавты** , а затем использовать **манипуляции** для перемещения отдельных блоков масти-космонавты, годится.
* Сказать **повернуть космонавты** для поворота элементы еще раз.
* Скажем **сброса модели** для возврата в исходную форму-космонавты, годится.

## <a name="the-end"></a>Конец

Поздравляем! Вы завершили **211 MR входные данные: Жест**.

* Вы знаете, как для обнаружения и реагирования для передачи событий отслеживания, перехода и обработки.
* Необходимо понимать разницу между жесты перехода и обработки.
* Вы знаете, как изменить курсор для предоставления визуальной обратной связи при обнаружении руки, при наличии будут потеряны, а если объект поддерживает различные взаимодействия (vs навигации манипуляции).
