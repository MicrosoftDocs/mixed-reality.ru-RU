---
title: Основы MR 101E - полный проект с помощью эмулятора
description: Выполните кодирование Пошаговое руководство по использованию Unity, Visual Studio и эмулятора HoloLens, чтобы ознакомиться с основами holographic приложения.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Смешанная реальность, смешанная реальность Windows, HoloLens, голограмма academy, руководства, эмулятор
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599406"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a>Общие сведения об MR 101E: Полный проект с помощью эмулятора

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

Этот учебник поможет в проекте, встроенные в Unity, который демонстрирует основные возможности Windows Mixed Reality, в том числе HoloLens [помощи](gaze.md), [жесты](gestures.md), [голоса](voice-input.md), [пространственных звук](spatial-sound.md) и [пространственное сопоставление](spatial-mapping.md). Руководства займет примерно 1 час.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td>Общие сведения об MR 101E: Полный проект с помощью эмулятора</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>предварительные требования

* ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) требуемые для проекта. Требуется компонент Unity 2017.2 или более поздней версии.
  * Если вам по-прежнему требуется поддержка Unity 5.6, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Если вам по-прежнему требуется поддержка Unity 5.5, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Если вам по-прежнему требуется поддержка Unity 5.4, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Удаление архива файлы рабочего стола или других легко положения. Оставьте имя папки в качестве **Origami**.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Глава 1 - world «Holo»

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

В этой главе мы установки наш первый проект Unity и пошагово выполнять построение и развертывание процесса.

### <a name="objectives"></a>Цели

* Настройка Unity для holographic разработки.
* Сделайте голограмма.
* См. в разделе голограмма, созданную.

### <a name="instructions"></a>Инструкция

* Запустите Unity.
* Выберите **откройте**.
* Введите расположение как **Origami** папку вы ранее не архивные.
* Выберите **Origami** и нажмите кнопку **Выбор папки**.
* Сохраните новую сцену: **Файл** / **сохранить сцену как**.
* Присвойте сцене имя **Origami** и нажмите клавишу **Сохранить** кнопки.

#### <a name="setup-the-main-camera"></a>Настройка главной камеры

* В **панели иерархии**выберите **Main Camera**.
* В **инспектор** задайте его положение преобразования **0,0,0**.
* Найти **очистить флаги** свойство и измените раскрывающийся список из **Skybox** для **Одноцветная**.
* Щелкните **фона** поля, чтобы открыть палитру цветов.
* Задайте **R, G, B и A** для **0**.

#### <a name="setup-the-scene"></a>Программа установки сцены

* В **панели иерархии**, щелкните **создать** и **создать пустой**.
* Щелкните правой кнопкой мыши новый **GameObject** и выберите Переименовать. Переименовать объект GameObject, чтобы **OrigamiCollection**.
* Из **голограммы** папку в **панель проекта**:
  * Перетащите **этап** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.
  * Перетащите **Sphere1** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.
  * Перетащите **Sphere2** в иерархию, чтобы быть дочерним элементом **OrigamiCollection**.
* Щелкните правой кнопкой мыши **направленный свет** объекта в **панели иерархии** и выберите **удалить**.
* Из **голограммы** папки, перетащите **индикаторы** в корне **панели иерархии**.
* В **иерархии**выберите **OrigamiCollection**.
* В **инспектор**, задайте положение преобразования **0, -0,5, 2.0**.
* Нажмите клавишу **воспроизведение** кнопки в Unity для предварительного просмотра вашего голограммы.
* Вы увидите Origami объекты в окне предварительного просмотра.
* Нажмите клавишу **воспроизведение** второй раз, чтобы выйти из режима предварительного просмотра.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Экспортировать проект из Unity в Visual Studio

* В Unity выберите **файл > Параметры сборки**.
* Выберите **Windows Store** в **платформы** списке и нажмите кнопку **переключить платформу**.
* Задайте **SDK** для **универсальной 10** и **тип сборки** для **D3D**.
* Проверьте **Unity C# проекты**.
* Нажмите кнопку **добавьте откройте сцены** Добавление сцены.
* Нажмите кнопку **параметры проигрывателя...** .
* В панели Инспектора выберите **логотип Windows Store**. Затем выберите **параметров публикации**.
* В **возможности** выберите **"микрофон"** и **SpatialPerception** возможности.
* В окне «Параметры построения» щелкните **построения**.
* Создание **новую папку** с именем «Приложение».
* Одним щелчком мыши **папки приложения**.
* Нажмите клавишу **выберите папку**.
* По завершении Unity появится окно проводника.
* Откройте **приложения** папки.
* Откройте **решение Visual Studio Origami**.
* С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **X86**.
  * Щелкните стрелку рядом с кнопкой на устройстве и выберите **HoloLens эмулятор**.
  * Нажмите кнопку **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.
  * Через некоторое время эмулятор, загрузится с помощью проекта Origami. При первом запуске [эмулятор](using-the-hololens-emulator.md), может занять до 15 минут для запуска эмулятора. Сразу после запуска, но закрывайте его.

## <a name="chapter-2---gaze"></a>Глава 2 - взглядом

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

В этой главе мы собираемся установки первого из трех способов взаимодействия с вашей голограммы-- [помощи](gaze.md).

### <a name="objectives"></a>Цели

* Визуализация вашей взглядом, с помощью курсора заблокирован в мире.

### <a name="instructions"></a>Инструкция

* Вернитесь к проекту Unity и закрыть окно Параметры построения, если он по-прежнему открыт.
* Выберите **голограммы** папку в **панель проекта**.
* Перетащите **курсор** в коллекцию **панели иерархии** на корневом уровне.
* Дважды щелкните **курсор** объекта более подробно рассмотрим вступили в силу.
* Щелкните правой кнопкой мыши **сценариев** папку «проект».
* Нажмите кнопку **создать** подменю.
* Выберите  **C# сценарий**.
* Назовите сценарий **WorldCursor**. Примечание. Имя обрабатывается с учетом регистра. Необходимо добавить расширение CS.
* Выберите **курсор** объекта в **панели иерархии**.
* Перетаскивание **WorldCursor** внесена в **панели Инспектора**.
* Дважды щелкните **WorldCursor** скрипт, чтобы открыть его в Visual Studio.
* Скопируйте и вставьте этот код в **WorldCursor.cs** и **сохранить все**.

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

* Перестройте приложение из **файл > Параметры сборки**.
* Вернитесь к ранее используется для развертывания в эмуляторе решение Visual Studio.
* Выберите «Обновить все» при появлении запроса.
* Нажмите кнопку **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.
* Для поиска вокруг сцены, используется контроллер Xbox. Обратите внимание на то, как курсор взаимодействует с форму объектов.

## <a name="chapter-3---gestures"></a>Глава 3 - жесты

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

В этой главе мы добавим поддержку [жесты](gestures.md). Когда пользователь выбирает сферы бумаги, сделаем сферы делятся, включив гравитации, с помощью обработчика физики Unity.

### <a name="objectives"></a>Цели

* Управлять вашей голограммы с выберите жестом.

### <a name="instructions"></a>Инструкция

Мы начнем путем создания скрипта, не может обнаружить выберите жест.

* В **сценарии** папки, создайте сценарий с именем **GazeGestureManager**.
* Перетащите **GazeGestureManager** скрипт на **OrigamiCollection** объект в иерархии.
* Откройте **GazeGestureManager** сценариев в Visual Studio и добавьте следующий код:

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

* Создание другого сценария в папке Scripts, это время с именем **SphereCommands**.
* Разверните **OrigamiCollection** объекта в иерархическом представлении.
* Перетащите **SphereCommands** скрипт на **Sphere1** объект на панели «иерархии».
* Перетащите **SphereCommands** скрипт на **Sphere2** объект на панели «иерархии».
* Откройте скрипт в Visual Studio для редактирования и замените код по умолчанию это:

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

* Экспорт, создавайте и развертывайте приложения в эмуляторе HoloLens.
* Оглядитесь сцены; центр на одном из сферы.
* Нажмите клавишу **A** кнопку на Xbox контроллере или клавишу ПРОБЕЛ, чтобы имитировать выберите жест.

## <a name="chapter-4---voice"></a>Глава 4 – голоса

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

В этой главе мы добавим поддержку для двух [голосовые команды](voice-input.md): Возвращает «Сброс world», чтобы удаленные как шары, расположенные в их исходное расположение и «Drop sphere» чтобы делятся сферы.

### <a name="objectives"></a>Цели

* Добавьте голосовые команды, которые всегда ожидать передачи данных в фоновом режиме.
* Создайте голограмма, на которое реагирует на команды голосом.

### <a name="instructions"></a>Инструкция

* В **сценарии** папки, создайте сценарий с именем **SpeechManager**.
* Перетащите **SpeechManager** скрипт на **OrigamiCollection** объект в иерархии
* Откройте **SpeechManager** скриптов в Visual Studio.
* Скопируйте и вставьте этот код в **SpeechManager.cs** и **сохранить все**:

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

* Откройте **SphereCommands** скриптов в Visual Studio.
* Обновите сценарий следующим образом:

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

* Экспорт, создавайте и развертывайте приложения в эмуляторе HoloLens.
* Эмулятор будет поддерживать "микрофон" компьютер и отвечать на ваш голос: настроить представление, чтобы курсор находится на одном из сферы, и сказать «Drop Sphere».
* Сказать «**Сброс World**"Чтобы вернуть их обратно в их начальной позиции.

## <a name="chapter-5---spatial-sound"></a>Глава 5 - Пространственные звука

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

В этой главе мы добавить музыку в приложение и затем активировать звуковые эффекты на определенные действия. Мы будем использовать [пространственных звук](spatial-sound.md) для предоставления звуков на определенное расположение в трехмерном пространстве.

### <a name="objectives"></a>Цели

* Услышать голограммы в ваш мир.

### <a name="instructions"></a>Инструкция

* В верхнем меню выберите Unity **изменить > Параметры проекта > аудио**
* Найти **подключаемый модуль Spatializer** задание и выберите **MS HRTF Spatializer**.
* Из **голограммы** папки, перетащите **окружением** объекта на **OrigamiCollection** объект на панели «иерархии».
* Выберите **OrigamiCollection** и найти **источника аудио** компонента. Измените следующие свойства:
  * Проверьте **Spatialize** свойство.
  * Проверьте **играть на переходит в спящий режим**.
  * Изменение **пространственных Blend** для **3D** путем перетаскивания бегунка вплоть до справа.
  * Проверьте **цикл** свойство.
  * Разверните **3D Параметры звука**и введите **0,1** для **Doppler уровень**.
  * Задайте **Rolloff тома** для **логарифмической Rolloff**.
  * Задайте **максимальное расстояние** для **20**.
* В **сценарии** папки, создайте сценарий с именем **SphereSounds**.
* Перетащите **SphereSounds** для **Sphere1** и **Sphere2** объектов в иерархии.
* Откройте **SphereSounds** в Visual Studio, измените следующий код и **сохранить все**.

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

* Сохраните сценарий и вернуться к Unity.
* Экспорт, создавайте и развертывайте приложения в эмуляторе HoloLens.
* Надеть наушники получить полные результаты и переместить ближе и максимально далеко от рабочей области звуковое изменить.

## <a name="chapter-6---spatial-mapping"></a>Глава 6 - пространственных сопоставление

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

Теперь мы собираемся использовать [пространственное сопоставление](spatial-mapping.md) снабдить реальный объект в реальном мире игровое поле.

### <a name="objectives"></a>Цели

* Можно открыть в реальном мире в виртуальный мир.
* Поместите вашей голограммы, где они наиболее важны для вас.

### <a name="instructions"></a>Инструкция

* Щелкните **голограммы** папку «проект».
* Перетащите **пространственных сопоставление** активов в корне **иерархии**.
* Щелкните **пространственных сопоставление** объект в иерархии.
* В **панели Инспектора**, измените следующие свойства:
  * Проверьте **рисования сетки Visual** поле.
  * Найдите **рисования материал** и щелкните этот кружок в правой части. Тип "**каркас**" в поле поиска вверху. Щелкните результат, а затем закройте окно.
* Экспорт, создавайте и развертывайте приложения в эмуляторе HoloLens.
* При запуске приложения, сетка ранее отсканированных реальных гостиной отображается в области каркаса.
* Смотрите, как последовательное сферы попадает off рабочей области, а также на пол!

Теперь мы покажем, как переместить OrigamiCollection в новое расположение:

* В **сценарии** папки, создайте сценарий с именем **TapToPlaceParent**.
* В **иерархии**, разверните **OrigamiCollection** и выберите **этап** объекта.
* Перетащите **TapToPlaceParent** скрипт на объект, к рабочей области.
* Откройте **TapToPlaceParent** сценариев в Visual Studio и обновить его следующим:

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

* Экспорт, построения и развертывания приложения.
* Теперь теперь можно поместить игры в определенном расположении путем gazing на него, используя Select жестов (**объект** или пробел) и перемещения в новое расположение и еще раз с помощью Select жест.

## <a name="the-end"></a>Конец

И это, чтобы в конце этого руководства!

Вы узнали:

* Как создать приложение holographic в Unity.
* Как сделать использование взглядом, жест, голоса, звуки и пространственное сопоставление.
* Как создавать и развертывать приложения с помощью Visual Studio.

Теперь вы готовы приступить к созданию собственных holographic приложений!

## <a name="see-also"></a>См. также

* [Общие сведения об MR 101: Полный проект с устройством](holograms-101.md)
* [Взглядом](gaze.md)
* [Жесты](gestures.md)
* [Голосовой ввод](voice-input.md)
* [Пространственные звука](spatial-sound.md)
* [Пространственное сопоставление](spatial-mapping.md)
