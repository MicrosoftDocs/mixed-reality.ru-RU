---
title: Входные данные MR 212 - Voice
description: Выполнения данного кода пошагового руководства, с помощью Unity, Visual Studio и HoloLens Дополнительные сведения о концепции голоса.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, учебник, голоса
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598926"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br>

# <a name="mr-input-212-voice"></a>Входные данные MR 212: Голосовые команды

[Голоса](voice-input.md) дает нам еще один способ взаимодействия с нашей голограммы. Голосовые команды работают в это очень естественный и простой способ. Разработка вашей голосовые команды, чтобы они были.

* Естественное
* Легко запомнить
* Контекста, соответствующего
* Достаточной степени отличаются от других параметров, в том же контексте

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

В [101 основы MR](holograms-101.md), мы использовали KeywordRecognizer создавать две простые голосовые команды. В 212 MR входных данных, мы Погрузитесь глубже и узнайте, как:

* Голосовые команды разработки, которые оптимизированы для распознавания речи HoloLens.
* Оповестить пользователя голоса, какие команды доступны.
* Подтверждаю, что мы слышали пользователя голосовых команд.
* Сведения о возможностях, пользователю о том, используя распознаватель диктовки.
* Используйте распознаватель грамматики для прослушивания на основе файла SRGS или спецификации грамматики распознавания речи, команды.

В этом курсе мы вернемся к обозреватель модели, который мы создали в [210 ввода MR](holograms-210.md) и [211 ввода MR](holograms-211.md).

>[!IMPORTANT]
>Видео, внедренных в каждой главы ниже были записаны с использованием более старой версии Unity и смешанной реальности Toolkit. Хотя пошаговые инструкции и точной и актуальной, может появиться скрипты и визуальные элементы в соответствующих видео, становятся недействительными. Видеоролики остаются включены перемешаны и поскольку рассматриваются основные понятия по-прежнему применяются.


## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td>Входные данные MR 212: Голосовые команды</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>Предварительные требования

* ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).
* Основные C# возможности программирования.
* Необходимо завершить [101 основы MR](holograms-101.md).
* Необходимо завершить [210 ввода MR](holograms-210.md).
* Необходимо завершить [211 ввода MR](holograms-211.md).
* Устройство HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) требуемые для проекта. Требуется компонент Unity 2017.2 или более поздней версии.
* Удаление архива файлы рабочего стола или других легко положения.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Список ошибок и примечания

* «Включить только мой код» необходимо отключить (*unchecked*) в Visual Studio в разделе Сервис -> Параметры -> Отладка для точки останова в коде.

## <a name="unity-setup"></a>Программа установки Unity

### <a name="instructions"></a>Инструкция

1. Запустите Unity.
2. Выберите **откройте**.
3. Перейдите к **HolographicAcademy-голограммы-212-Voice** папку вы ранее не архивные.
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

## <a name="chapter-1---awareness"></a>Глава 1 - Awareness

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Цели

* Узнайте, **и запреты** голосовые команды разработки.
* Используйте **KeywordRecognizer** добавить взглядом на основе голосовые команды.
* Оповестить пользователей о голосовых команд, с помощью курсора **отзывы**.

### <a name="voice-command-design"></a>Конструктор голосовых команд

В этой главе вы узнаете о разработке голосовых команд. При создании голосовые команды:

#### <a name="do"></a>DO

* Создайте краткую команд. Вы не хотите использовать *«В этом видео текущего выбранного»*, так как эта команда не является кратким и легко нужно уделять внимание пользователем. Вместо этого следует использовать: *«Воспроизвести видео»*, так как он очень четкий и имеет несколько слоги.
* Используйте простой словаря. Всегда пытаться использовать часто употребляемых слов и фраз, которые просты для пользователя для обнаружения и запомнить. Например, если приложение должно было объект примечание, который может отобразить или скрыть из представления, не используется команда *«Показать панель»*, так как это редко используемый термин «таблицы». Вместо этого выполнить команду: *«Показать заметки»*, чтобы отобразить Примечание в приложении.
* Соблюдать единообразие. Голосовые команды должны поддерживать согласованность всего приложения. Допустим, у вас есть два сцен в приложении и оба сцены быть кнопка для закрытия приложения. Если первую сцену использовала команду *«Выход»* для активации кнопки, а второй сцены использовала команду *«Закрыть приложение»*, то пользователь будет крайне запутанным. Если те же функциональные возможности сохраняется между сцены, затем ту же команду голосовой следует использовать для его запуска.

#### <a name="dont"></a>НЕ НАДО

* Используйте единый слог команды. Например, при создании голосовых команд для воспроизведения видео, старайтесь не использовать простую команду *«Play»*, так как он является только единый слог и легко могут быть пропущены в системе. Вместо этого следует использовать: *«Воспроизвести видео»*, так как он очень четкий и имеет несколько слоги.
* Команды системы. *«Select»* команда зарезервировано системой для Активация события касания для выделенного объекта. Не используйте *«Select»* команда в ключевое слово или фразу, как оно может не работать, как ожидается. Например, если голосовые команды для выбора куба в приложении была *«Выберите куб»*, но пользователь смотрел сферы при их распространенная команды, то вместо этого будет выбрано сферы. Кроме того, приложения на панели команд, включена ли голосовая связь. Не используйте следующие команды речи в представлении CoreWindow:
    1. Вернуться
    2. Средство прокрутки
    3. Средство масштабирования
    4. Инструмент «перетаскивание»
    5. Регулировка
    6. Удалить
* Используйте аналогичные звуков. Следует избегать использования голосовых команд, взять. Если у вас есть приложение о покупках поддерживавших *«Показать Store»* и *«Больше»* как голосовые команды, то необходимо отключить одну из команд, пока другой использовался. Например, можно использовать *«Показать Store»* кнопку для открытия хранилища, а затем отключить этой команды, когда было отображено хранилище, чтобы *«Больше»* команда может быть использована для просмотра.

### <a name="instructions"></a>Инструкция

* В Unity **иерархии** панели, воспользуйтесь средством поиска для поиска **holoComm_screen_mesh** объекта.
* Дважды щелкните **holoComm_screen_mesh** объект для просмотра его в **сцены**. Это watch космонавты, который ответит на наших голосовые команды.
* В **инспектор** панели, найдите **источника ввода речи (скрипт)** компонента.
* Разверните **ключевые слова** раздел, чтобы просмотреть поддерживаемые голосовых команд: **Откройте Communicator**.
* Щелкните значок шестеренки справа, а затем выберите **изменить скрипт**.
* Изучите **SpeechInputSource.cs** чтобы понять, как он использует **KeywordRecognizer** добавить голосовые команды.

### <a name="build-and-deploy"></a>Создание и развертывание

* В Unity, использовать **файл > Параметры сборки** для перестроения приложения.
* Откройте **приложения** папки.
* Откройте **решение ModelExplorer в Visual Studio**.

(Если вы уже сборки и развертывания этого проекта в Visual Studio во время установки, затем можно открыть этот экземпляр VS и нажмите кнопку «Обновить все» при появлении запроса).

* В Visual Studio щелкните **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.
* После развертывания приложения для HoloLens, закрыть окна соответствия с помощью [жест касания](gestures.md#air-tap) жест.
* Помощи в космонавты контрольных значений.
* Когда часами в фокусе, убедитесь, что вид курсора меняется в микрофон. Это обеспечивает обратную связь, приложение ожидает передачи данных для голосовых команд.
* Убедитесь, что появляется подсказка в watch. Это позволяет пользователям обнаруживать *«Open Communicator»* команды.
* При gazing в часы, скажем *«Откройте Communicator»* Открытие панели communicator.

## <a name="chapter-2---acknowledgement"></a>Глава 2 - подтверждения

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Цели

* Запишите сообщения с помощью ввода от микрофона.
* Отправить отзыв для пользователя, которого приложение ожидает передачи голоса.

>[!NOTE]
>**"Микрофон"** возможность должны объявляться для приложения для записи с микрофона. Для этого вам уже в 212 MR входных данных, но имейте это в виду для ваших собственных проектов.
>
>1. В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»
>2. Перейдите на вкладку «Универсальной платформы Windows»
>3. В разделе «Возможности публикации > Параметры» установите флажок **"микрофон"** возможностей

### <a name="instructions"></a>Инструкция

* В Unity **иерархии** панели, убедитесь, что **holoComm_screen_mesh** выбран объект.
* В **инспектор** панели, найти **-космонавты, годится Watch (скрипт)** компонента.
* Щелкните Мелкая "," синий куба, который имеет значение для параметра **Communicator Prefab** свойство.
* В **проекта** панели **Communicator** prefab теперь должны иметь фокус.
* Щелкните **Communicator** prefab в **проекта** панели для просмотра его компонентов в **инспектор**.
* Рассмотрим **Manager "микрофон" (сценарий)** компонента, это позволит нам записать голос пользователя.
* Обратите внимание, что **Communicator** объект имеет **обработчик речи входных данных (скрипт)** компонент за реагирование на **Отправка сообщения** команды.
* Рассмотрим **Communicator (скрипт)** компонента и дважды щелкните его, чтобы открыть его в Visual Studio.

Communicator.cs отвечает за настройку состояния соответствующие кнопки, communicator устройства. Это позволит пользователям записывать сообщения, воспроизведите его и отправить сообщение-космонавты, годится. Он также будет запускать и останавливать форму анимированных wave для подтверждения для пользователя, их мнение.

* В **Communicator.cs**, удалите следующие строки (81 и 82) из **запустить** метод. Это позволит кнопки «Запись» на communicator.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Создание и развертывание

* В Visual Studio перестройте свое приложение и развернуть на устройстве.
* Помощи в космонавты контрольных значений и сказать *«Open Communicator»* Показать communicator.
* Нажмите клавишу **записи** кнопку (микрофон) для начала записи устные сообщение для-космонавты, годится.
* Начните говорить и убедитесь, что волна анимация воспроизводится на communicator, который предоставляет отзывы пользователю их мнение.
* Нажмите клавишу **остановить** (левый квадрат) и убедитесь, что анимация wave останавливается.
* Нажмите клавишу **воспроизведение** кнопку (Прямоугольный треугольник), чтобы воспроизвести записанные сообщения и получить ваш отзыв на устройстве.
* Нажмите клавишу **остановить** кнопку (правом квадрат), чтобы остановить воспроизведение записанных сообщения.
* Скажем *«Отправить сообщение»* закрыть communicator и получать ответ сообщение получено от-космонавты, годится.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Глава 3 - основные сведения о и распознаватель диктовки

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Цели

* Используйте распознаватель диктовки для преобразования пользователя речи в текст.
* Показать распознаватель диктовки нулевой гипотезы и конечный результаты в communicator.

В этой главе мы будем использовать распознаватель диктовки для создания сообщения для-космонавты, годится. При использовании распознавателя диктовки, имейте в виду, что:

* Вы должны быть подключены к Wi-Fi для распознавателя диктовки для работы.
* Истекает время ожидания после заданного периода времени. Существует два времени ожидания, которые следует учитывать:
  * Если распознаватель запускается не слышит аудио для первых пяти секунд, истечет.
  * Если распознаватель дала результат, но затем слышит бездействия в течение 20 секунд, время ожидания истекает.
* Одновременно можно запустить только один тип распознавателя (ключевое слово или речевые сообщения).

>[!NOTE]
>**"Микрофон"** возможность должны объявляться для приложения для записи с микрофона. Для этого вам уже в 212 MR входных данных, но имейте это в виду для ваших собственных проектов.
>
>1. В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»
>2. Перейдите на вкладку «Универсальной платформы Windows»
>3. В разделе «Возможности публикации > Параметры» установите флажок **"микрофон"** возможностей

### <a name="instructions"></a>Инструкция

Мы собираемся изменить **MicrophoneManager.cs** использовать распознаватель диктовки. Это, мы добавим:

1. Когда **кнопку записи** является нажата, мы будем **запустить DictationRecognizer**.
2. Показать **гипотезы** из DictationRecognizer понятны.
3. Блокировка в **результаты** из DictationRecognizer понятны.
4. Проверьте наличие времени ожидания из DictationRecognizer.
5. Когда **"Остановить"** нажата, или время ожидания, сеанса mic **остановить DictationRecognizer**.
6. Перезапустите **KeywordRecognizer**, который будет прослушивать **Отправка сообщения** команды.

Начнем. Завершить все упражнений по кодированию для 3.a в **MicrophoneManager.cs**, или скопируйте и вставьте код завершения, найти ниже:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Создание и развертывание

* В Visual Studio и разверните на ваше устройство.
* Закройте окно соответствия с помощью жеста жест касания.
* Помощи в космонавты контрольных значений и сказать *«Open Communicator»*.
* Выберите **записи** кнопки (микрофон) для записи сообщения.
* Начните говорить. **Распознаватель диктовки** будет интерпретировать речи и отображать текст нулевой гипотезы в communicator.
* Попробуйте указать *«Отправить сообщение»* при записи сообщения. Обратите внимание, что **распознаватель ключевое слово** не отвечает, так как **распознаватель диктовки** по-прежнему активна.
* Остановите проговаривание на несколько секунд. Следите за диктовки распознаватель завершает его гипотезы и показан окончательный результат.
* Начать разговор, а затем сделать паузу на 20 секунд. Это приведет к **распознаватель диктовки** истечение времени ожидания.
* Обратите внимание, что **распознаватель ключевое слово** будет снова включена после выше времени ожидания. Communicator теперь будет отвечать на голосовые команды.
* Скажем *«Отправить сообщение»* для отправки сообщения-космонавты, годится.

## <a name="chapter-4---grammar-recognizer"></a>Глава 4 – грамматики распознавания

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Цели

* Используйте распознаватель грамматику для распознавания речи пользователя в соответствии с файла SRGS или спецификации грамматики распознавания речи.

>[!NOTE]
>**"Микрофон"** возможность должны объявляться для приложения для записи с микрофона. Для этого вам уже в 212 MR входных данных, но имейте это в виду для ваших собственных проектов.
>
>1. В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»
>2. Перейдите на вкладку «Универсальной платформы Windows»
>3. В разделе «Возможности публикации > Параметры» установите флажок **"микрофон"** возможностей

### <a name="instructions"></a>Инструкция

1. В **иерархии** панели, поиск **Jetpack_Center** и выберите его.
2. Найдите **свои действия** скрипта в **инспектор** панели.
3. Щелкните маленький кружок в правой части **объекта в тег вдоль** поля.
4. В открывшемся окне Поиск **SRGSToolbox** и выберите его из списка.
5. Взгляните на **SRGSColor.xml** файл **StreamingAssets** папки.
* Спецификации SRGS разработки можно найти на веб-сайте W3C [здесь](https://www.w3.org/TR/speech-grammar/).
* В наш файл SRGS у нас есть три типа правил:
  * Правило, которое позволяет вам сказать один цвет из списка двенадцать цветов.
  * Три правила, которые прослушивают сочетание правила цвета и одну из трех фигур.
  * Корневое правило colorChooser, который ожидает передачи любое сочетание трех правил «цвет + фигуры». Фигуры можно сказать, что в любом порядке и в любой суммы от лишь одна всем трем. Это единственное правило, которое будет отслеживаться, как оно указано в качестве корневого правила в верхней части файла исходную &lt;грамматики&gt; тега.

### <a name="build-and-deploy"></a>Создание и развертывание

* Перестройте приложение в Unity, а затем построить и развернуть из Visual Studio, чтобы оценить приложение в HoloLens.
* Закройте окно соответствия с помощью жеста жест касания.
* Помощи в jetpack космонавты и сделайте жест жест касания.
* Начните говорить. **Грамматики распознавания** будет интерпретировать речи и изменить цвета фигуры, основаны на предположении. Пример команды — «синий круг, Желтый квадрат».
* Сделайте другой жест жест касания для закрытия панели элементов.

## <a name="the-end"></a>Конец

Поздравляем! Вы завершили **212 MR входные данные: Голосовые**.

* Вы знаете, рекомендации и запреты голосовых команд.
* Вы узнали, как всплывающие подсказки были, применяемых в информировании пользователей голосовых команд.
* Вы видели несколько видов обратной связи, используется для подтверждения, что голос пользователя был слышали.
* Вы знаете, как переключиться между распознаватель ключевое слово и распознаватель диктовки, а также как эти две возможности понимать и интерпретировать ваш голос.
* Вы узнали, как использовать файл SRGS и распознаватель грамматику для распознавания речи в приложении.
