---
title: Основные сведения о 101E — завершение проекта с помощью эмулятора
description: Выполните это пошаговое руководство по программированию с помощью Unity, Visual Studio и эмулятора HoloLens, чтобы изучить основные принципы работы с приложением Holographic.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Смешанная реальность, Windows Mixed Reality, HoloLens, голограмма, Academy, учебник, эмулятор
ms.openlocfilehash: b1d8e1f3f272051bdd6f69ab88c3aef4f86f13ef
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434703"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Для HoloLens 2 опубликована [Новая серия руководств](mrlearning-base.md) .

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a>Основные сведения о 101E: завершение проекта с помощью эмулятора

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

В этом руководстве описывается полный проект, встроенный в Unity, демонстрирующий основные функции Windows Mixed Reality в HoloLens, включая [взгляд](gaze-and-commit.md), [жесты](gaze-and-commit.md#composite-gestures), [речевой ввод](voice-input.md), [Пространственный звук](spatial-sound.md) и [пространственное сопоставление](spatial-mapping.md) . . Выполнение руководства займет примерно 1 час.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td>Основные сведения о 101E: завершение проекта с помощью эмулятора</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>Необходимые условия

* КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) , необходимые для проекта. Требуется Unity 2017,2 или более поздней версии.
  * Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Отмена архивации файлов на Рабочий стол или другого места для удобства доступа. В качестве имени папки используйте **Origami**.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Глава 1-"Холо"

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

В этой главе мы создадим наш первый проект Unity и пошаговым процессом сборки и развертывания.

### <a name="objectives"></a>Задачи

* Настройка Unity для разработки с Holographic.
* Создайте голограмму.
* Ознакомьтесь с созданной голограммой.

### <a name="instructions"></a>Инструкция

* Запустите Unity.
* Нажмите кнопку **Открыть**.
* Введите Location в качестве папки **Origami** , которая была отменена для архивации.
* Выберите **Origami** и щелкните **выбрать папку**.
* Сохраните новую сцену: **файл** / **сохранить сцену как**.
* Присвойте сцене имя **Origami** и нажмите кнопку **Save (сохранить** ).

#### <a name="setup-the-main-camera"></a>Настройка основной камеры

* На **панели Иерархия**выберите **Главная камера**.
* В **инспекторе** задайте для его параметра «transform **» значение 0, 0,** 0.
* Найдите свойство **clear flags** и измените раскрывающийся список с **скибокс** на **сплошной цвет**.
* Щелкните поле **Background (фон** ), чтобы открыть палитру цветов.
* Задайте значения **R, G, B и A** равными **0**.

#### <a name="setup-the-scene"></a>Настройка сцены

* На **панели Иерархия**щелкните **создать** и **создать пустой**.
* Щелкните правой кнопкой мыши новый **GameObject** и выберите команду Переименовать. Переименуйте GameObject в **оригамиколлектион**.
* Из папки **голограмм** на **панели проекта**:
  * Перетащите **этап** в иерархию, чтобы он был дочерним элементом **оригамиколлектион**.
  * Перетащите **Sphere1** в иерархию, чтобы она была дочерней для **оригамиколлектион**.
  * Перетащите **Sphere2** в иерархию, чтобы она была дочерней для **оригамиколлектион**.
* Щелкните правой кнопкой мыши **направленный объект Light** на **панели Иерархия** и выберите команду **Удалить**.
* Перетащите **индикаторы** из папки **голограммы** в корневую папку **панели Иерархия**.
* В **иерархии**выберите **оригамиколлектион**.
* В **инспекторе**задайте для параметра Расположение преобразования значение **0,-0,5, 2,0**.
* Нажмите кнопку **воспроизвести** в Unity, чтобы просмотреть голограммы.
* В окне предварительного просмотра должны отобразиться объекты Origami.
* Чтобы выйти из режима предварительного просмотра, нажмите кнопку **воспроизвести** еще раз.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Экспорт проекта из Unity в Visual Studio

* В Unity выберите **файл > параметры сборки**.
* Выберите **Магазин Windows** в списке **платформа** и щелкните **Переключить платформу**.
* Задайте для **пакета SDK** значение **универсальное 10** , а для **типа сборки** — **D3D**.
* Проверьте **проекты C# Unity**.
* Щелкните **Добавить открытые сцены** , чтобы добавить сцену.
* Щелкните **Параметры проигрывателя...** .
* На панели инспектора выберите **логотип магазина Windows**. Затем выберите **Параметры публикации**.
* В разделе **возможности** выберите возможности **микрофона** и **спатиалперцептион** .
* Вернувшись в окно параметры сборки, щелкните **Сборка**.
* Создайте **новую папку** с именем App.
* Щелкните **папку приложения**одним щелчком мыши.
* Нажмите кнопку **выбрать папку**.
* После завершения Unity появится окно проводника.
* Откройте папку **приложения** .
* Откройте **решение Origami Visual Studio**.
* С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.
  * Щелкните стрелку рядом с кнопкой устройство и выберите **эмулятор HoloLens**.
  * Щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.
  * Через некоторое время эмулятор начнет работу с проектом Origami. При первом запуске [эмулятора](using-the-hololens-emulator.md)для запуска эмулятора может потребоваться до 15 минут. После запуска не закрывайте его.

## <a name="chapter-2---gaze"></a>Глава 2. взгляд

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

В этой главе мы будем познакомиться с первым из трех способов взаимодействия с голограммами — [Взгляните](gaze-and-commit.md).

### <a name="objectives"></a>Задачи

* Визуализируйте взгляд с помощью курсора, заблокированного по всему миру.

### <a name="instructions"></a>Инструкция

* Вернитесь к проекту Unity и закройте окно параметры сборки, если оно все еще открыто.
* Выберите папку **голограммы** на **панели проект**.
* Перетащите объект **курсора** на **панель Иерархия** на корневом уровне.
* Дважды щелкните объект **курсора** , чтобы просмотреть его Подробнее.
* Щелкните правой кнопкой мыши папку **сценарии** на панели проект.
* Щелкните подменю **создать** .
* Выберите  **C# скрипт**.
* Назовите сценарий **ворлдкурсор**. Примечание. в имени учитывается регистр. Добавлять расширение CS не требуется.
* Выберите объект **курсора** на **панели Иерархия**.
* Перетащите сценарий **ворлдкурсор** на **Панель инспектора**.
* Дважды щелкните скрипт **ворлдкурсор** , чтобы открыть его в Visual Studio.
* Скопируйте и вставьте этот код в **WorldCursor.CS** и **Сохраните все**.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* Перестройте приложение из **файла > параметры сборки**.
* Вернитесь к решению Visual Studio, которое ранее использовалось для развертывания в эмуляторе.
* При появлении запроса выберите "перезагрузить все".
* Щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.
* Используйте контроллер Xbox для просмотра сцены. Обратите внимание, что курсор взаимодействует с формой объектов.

## <a name="chapter-3---gestures"></a>Глава 3 — жесты

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

В этой главе мы добавим поддержку [жестов](gaze-and-commit.md#composite-gestures). Когда пользователь выбирает бумажную сферу, мы сделаем сферу, включив для нее функцию "сила притяжения" с помощью системы обработки физических модулей Unity.

### <a name="objectives"></a>Задачи

* Контролируйте голограммы с помощью жеста выбора.

### <a name="instructions"></a>Инструкция

Начнем с создания сценария, чем может обнаружить жест выбора.

* В папке **Scripts** создайте скрипт с именем **газежестуреманажер**.
* Перетащите скрипт **газежестуреманажер** на объект **оригамиколлектион** в иерархии.
* Откройте скрипт **газежестуреманажер** в Visual Studio и добавьте следующий код:

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Создайте другой скрипт в папке Scripts с именем **сферекоммандс**.
* Разверните объект **оригамиколлектион** в представлении иерархии.
* Перетащите скрипт **сферекоммандс** на объект **Sphere1** на панели Иерархия.
* Перетащите скрипт **сферекоммандс** на объект **Sphere2** на панели Иерархия.
* Откройте скрипт в Visual Studio для редактирования и замените код по умолчанию следующим:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* Экспортируйте, создайте и разверните приложение в эмуляторе HoloLens.
* Взгляните на сцену и помещайтесь по центру на одном из шарик.
* Нажмите кнопку **на** контроллере Xbox или нажмите клавишу пробел, чтобы имитировать жест выбора.

## <a name="chapter-4---voice"></a>Глава 4-Voice

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

В этой главе мы добавим поддержку двух [голосовых команд](voice-input.md): "сбросить мир", чтобы вернуть удаленные шарик к их исходному расположению и "удалить шар", чтобы сделать сферу.

### <a name="objectives"></a>Задачи

* Добавление речевых команд, которые всегда прослушиваются в фоновом режиме.
* Создайте голограмму, которая реагирует на голосовую команду.

### <a name="instructions"></a>Инструкция

* В папке **Scripts** создайте скрипт с именем **спичманажер**.
* Перетащите скрипт **спичманажер** на объект **оригамиколлектион** в иерархии
* Откройте скрипт **спичманажер** в Visual Studio.
* Скопируйте и вставьте этот код в **SpeechManager.CS** и **Сохраните все**:

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Откройте скрипт **сферекоммандс** в Visual Studio.
* Обновите скрипт для чтения следующим образом:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* Экспортируйте, создайте и разверните приложение в эмуляторе HoloLens.
* Эмулятор будет поддерживать микрофон компьютера и отвечать на ваш голос: настройте представление таким образом, чтобы курсор наследовался на одном из шарик и сказал «Drop Sphere».
* Скажите «**сбросить мир**», чтобы вернуть их в исходное положение.

## <a name="chapter-5---spatial-sound"></a>Глава 5 — Пространственный звук

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

В этой главе мы добавим музыку в приложение, а затем активируем звуковые эффекты для определенных действий. Мы будем использовать [Пространственный звук](spatial-sound.md) , чтобы дать звуковое сопровождение определенному месту в трехмерном пространстве.

### <a name="objectives"></a>Задачи

* Прослушайте голограммы в своем мире.

### <a name="instructions"></a>Инструкция

* В элементе Unity выберите в верхнем меню **правка > параметры проекта > звук**
* Найдите параметр **подключаемого модуля спатиализер** и выберите **MS хртф спатиализер**.
* В папке **голограмм** перетащите объект **окружения** на объект **оригамиколлектион** на панели Иерархия.
* Выберите **оригамиколлектион** и найдите компонент " **источник аудио** ". Измените следующие свойства:
  * Проверьте свойство **спатиализе** .
  * Проверьте **Воспроизведение в спящем**режиме.
  * Измените **пространственный переход** на **3D** , перетащив ползунок вправо.
  * Проверьте свойство **Loop** .
  * Разверните **Параметры 3D Sound**и введите **0,1** для **уровня Doppler**.
  * Задайте для параметра **Volume роллофф** значение **логарифмической роллофф**.
  * Установите **Максимальное расстояние** равным **20**.
* В папке **Scripts** создайте скрипт с именем **сфересаундс**.
* Перетащите **сфересаундс** в объекты **Sphere1** и **Sphere2** в иерархии.
* Откройте **сфересаундс** в Visual Studio, обновите следующий код и **Сохраните все**.

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* Сохраните скрипт и вернитесь в Unity.
* Экспортируйте, создайте и разверните приложение в эмуляторе HoloLens.
* Выизнос наушников, чтобы получить полный результат, и продвинуться ближе и дальше от этапа, чтобы услышать смену звуков.

## <a name="chapter-6---spatial-mapping"></a>Глава 6-пространственное сопоставление

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

Теперь мы будем использовать [пространственное сопоставление](spatial-mapping.md) , чтобы поместить игровую доску на реальный объект в реальном мире.

### <a name="objectives"></a>Задачи

* Приведите реальный мир к виртуальному миру.
* Размещайте голограммы, где это важно.

### <a name="instructions"></a>Инструкция

* Щелкните папку **голограмм** на панели проект.
* Перетащите ресурс **пространственного сопоставления** в корень **иерархии**.
* Щелкните объект **пространственного сопоставления** в иерархии.
* На **панели инспектора**измените следующие свойства.
  * Установите флажок **рисовать визуальные сетки** .
  * Перейдите на вкладку **Рисование материалов** и щелкните окружность справа. Введите "**каркасная**схема" в поле поиска вверху. Щелкните результат, а затем закройте окно.
* Экспортируйте, создайте и разверните приложение в эмуляторе HoloLens.
* При запуске приложения сеть ранее проверенной в реальном времени области будет отображаться в каркасе.
* Следите за тем, как изкрутка будет выпадать за пределы этапа, и на этаж!

Теперь мы покажем, как переместить Оригамиколлектион в новое расположение:

* В папке **Scripts** создайте скрипт с именем **таптоплацепарент**.
* В **иерархии**разверните **оригамиколлектион** и выберите объект **Stage** .
* Перетащите скрипт **таптоплацепарент** на объект Stage.
* Откройте скрипт **таптоплацепарент** в Visual Studio и обновите его следующим образом:

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* Экспорт, сборка и развертывание приложения.
* Теперь вы можете разместить игру в определенном месте, облаками ее с помощью жеста выбора (**a** или пробела), а затем переместить в новое место и снова с помощью жеста выбора.

## <a name="the-end"></a>Конец

И это окончание этого руководства.

Вы узнали:

* Создание приложения holographic в Unity.
* Использование взгляда, жеста, голоса, звуков и пространственного сопоставления.
* Как создать и развернуть приложение с помощью Visual Studio.

Теперь вы готовы приступить к созданию собственных приложений holographic!

## <a name="see-also"></a>См. также

* [Основные сведения о MR 101: завершение проекта с помощью устройства](holograms-101.md)
* [Взгляд](gaze-and-commit.md)
* [Направление головы и фиксация](gaze-and-commit.md)
* [Голосовой ввод](voice-input.md)
* [Пространственный звук](spatial-sound.md)
* [Пространственное сопоставление](spatial-mapping.md)
