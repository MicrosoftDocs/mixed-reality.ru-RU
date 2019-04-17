---
title: Совместное использование 240 - несколько устройств HoloLens MR
description: Выполните кодирование Пошаговое руководство по использованию Unity, Visual Studio и HoloLens совместного использования голограммы подробные сведения.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, совместное использование, сетей, academy, руководство
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601389"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>Совместное использование 240 MR: Несколько устройств HoloLens

Голограммы, предоставленному присутствие в наш мир оставшихся в месте по мере продвижения в пространстве. HoloLens отслеживает голограммы на месте с использованием различных [системы координат](coordinate-systems.md) для отслеживания местоположение и ориентацию объектов. Когда мы совместно используют эти системы координат, между устройствами, мы можем создать общий интерфейс, который позволяет принять участие в общих holographic мире.

В этом руководстве мы выполним следующее.

* Настройка сети для общего качества.
* Совместное использование голограммы устройств HoloLens.
* Обнаружение других пользователей, общих holographic мира.
* Создайте общий пошаговой процедуры, где можно целевой другие игроки - и запускать летящими их!

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td>Совместное использование 240 MR: Несколько устройств HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>предварительные требования

* ПК Windows 10, настроены с правильным [установлены инструменты](install-the-tools.md) с доступом к Интернету.
* По крайней мере два устройства HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) требуемые для проекта. Требуется компонент Unity 2017.2 или более поздней версии.
  * Если вам по-прежнему требуется поддержка Unity 5.6, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Если вам по-прежнему требуется поддержка Unity 5.5, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Если вам по-прежнему требуется поддержка Unity 5.4, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Удаление архива файлы рабочего стола или других легко положения. Оставьте имя папки в качестве **SharedHolograms**.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Глава 1 - Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

В этой главе мы установки наш первый проект Unity и пошагово выполнять построение и развертывание процесса.

### <a name="objectives"></a>Цели

* Настройка Unity для разработки приложений holographic.
* См. в разделе вашей голограмма!

### <a name="instructions"></a>Инструкция

* Запустите Unity.
* Выберите **откройте**.
* Введите расположение как **SharedHolograms** папки, которые вы ранее архиве.
* Выберите **имя_проекта** и нажмите кнопку **Выбор папки**.
* В **иерархии**, щелкните правой кнопкой мыши **Main Camera** и выберите **удалить**.
* В **HoloToolkit-совместное использование-240/Prefabs/камеры** папки, найти **Main Camera** prefab.
* Перетаскивание **Main Camera** в **иерархии**.
* В **иерархии**, щелкните **создать** и **создать пустой**.
* Щелкните правой кнопкой мыши новый **GameObject** и выберите **Переименовать**.
* Переименовать объект GameObject, чтобы **HologramCollection**.
* Выберите **HologramCollection** объекта в **иерархии**.
* В **инспектор** задать **преобразование положения** для: **X: 0, Y: -0,25, Z: 2**.
* В **голограммы** папку в **панель проекта**, найти **EnergyHub** активов.
* Перетаскивание **EnergyHub** объекта из **панель проекта** для **иерархии** как **потомком HologramCollection**.
* Выберите **файл > Сохранить сцену как...**
* Присвойте сцене имя **SharedHolograms** и нажмите кнопку **Сохранить**.
* Нажмите клавишу **воспроизведение** кнопки в Unity для предварительного просмотра вашего голограммы.
* Нажмите клавишу **воспроизведение** второй раз, чтобы выйти из режима предварительного просмотра.

**Экспортировать проект из Unity в Visual Studio**
* В Unity выберите **файл > Параметры сборки**.
* Нажмите кнопку **добавьте откройте сцены** Добавление сцены.
* Выберите **универсальной платформы Windows** в **платформы** списке и нажмите кнопку **переключить платформу**.
* Задайте **SDK** для **универсальной 10**.
* Задайте **целевое устройство** для **HoloLens** и **тип сборки UWP** для **D3D**.
* Проверьте **Unity C# проекты**.
* Щелкните **Сборка**.
* В обозревателе файл создать **новую папку** с именем «Приложение».
* Одним щелчком мыши **приложения** папки.
* Нажмите клавишу **выберите папку**.
* По завершении Unity появится окно проводника.
* Откройте **приложения** папки.
* Откройте **SharedHolograms.sln** для запуска Visual Studio.
* С помощью верхней панели инструментов в Visual Studio, изменить целевой объект с отладки на **выпуска** и из ARM для **X86**.
* Щелкните стрелку раскрывающегося списка рядом с локального компьютера и выберите **удаленное устройство**.
    * Задайте **адрес** в имя или IP-адрес вашего HoloLens. Если вы не знаете IP-адрес устройства, найдите в **параметры > сеть и Интернет > Дополнительно** или попросить Cortana **«Привет, Кортана, что такое Мой IP-адрес?»**
    * Оставьте **режим проверки подлинности** присвоено **универсальной**.
    * Нажмите кнопку **выберите**
* Нажмите кнопку **Отладка > Запуск без отладки** или нажмите клавишу **Ctrl + F5**. Если это при первом развертывании к устройству, необходимо будет [свяжите его с помощью Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
* Поместите на вашей HoloLens и найти голограмма EnergyHub.

## <a name="chapter-2---interaction"></a>Глава 2 - взаимодействия

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

В этой главе мы будет взаимодействовать с нашей голограммы. Во-первых, мы добавим курсора для визуализации наших [помощи](gaze.md). Затем мы добавим [жесты](gestures.md) и используйте позаниматься для размещения наших голограммы в пространстве.

### <a name="objectives"></a>Цели

* Используйте взглядом входных данных для управления курсором.
* Используйте жест ввода для взаимодействия с голограммы.

### <a name="instructions"></a>Инструкция

**Взглядом**
* В **панели иерархии** выберите **HologramCollection** объекта.
* В **панели Инспектора** щелкните **добавить компонент** кнопки.
* В меню, введите в поле поиска **помощи Manager**. Выберите результат поиска.
* В **совместное использование 240\Prefabs\Input HoloToolkit** папки, найти **курсор** активов.
* Перетаскивание **курсор** активов на **иерархии**.

**Жест**
* В **панели иерархии** выберите **HologramCollection** объекта.
* Нажмите кнопку **добавить компонент** и тип **Manager жест** в поле поиска. Выберите результат поиска.
* В **панели иерархии**, разверните **HologramCollection**.
* Выберите дочерние **EnergyHub** объекта.
* В **панели Инспектора** щелкните **добавить компонент** кнопки.
* В меню, введите в поле поиска **голограмма размещения**. Выберите результат поиска.
* Сохраните сцену, выбрав **файл > Сохранить сцену**.

**Развертывание и наслаждайтесь**
* Создание и развертывание в вашей HoloLens, следуя инструкциям в предыдущей главе.
* После запуска приложения на вашей HoloLens перемещать голове и обратите внимание на то, как EnergyHub соответствует вашей взглядом.
* Обратите внимание на то, как выглядит при помощи при голограмма курсора и изменяется на Точечный свет, если не gazing в голограмма.
* Выполните жест касания для размещения голограмма. В настоящее время в нашем проекте можно установить только один раз голограмма (повторное развертывание на попытку).

## <a name="chapter-3---shared-coordinates"></a>Глава 3 - Shared координирует

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Он см. в разделе и взаимодействовать с голограммы вряд ли двигаться дальше. Мы составим наш первый опытом - голограмма, которые можно будет увидеть друг с другом.

### <a name="objectives"></a>Цели

* Настройка сети для общего качества.
* Установите отправную точку.
* Совместное использование системы координат устройства.
* Каждый пользователь будет видеть же она!

>[!NOTE]
>**InternetClientServer** и **PrivateNetworkClientServer** возможности должны объявляться для приложения для подключения к серверу управления доступом. Для этого вам уже в голограммы 240, но имейте это в виду для ваших собственных проектов.
>1. В редакторе Unity, перейдите к параметрам проигрывателя, перейдя по адресу «Изменить > проекта Параметры > Player»
>2. Перейдите на вкладку «Windows Store»
>3. В разделе «Возможности публикации > Параметры» установите флажок **InternetClientServer** возможность и **PrivateNetworkClientServer** возможностей

### <a name="instructions"></a>Инструкция

* В **панель проекта** перейдите к **совместное использование 240\Prefabs\Sharing HoloToolkit** папки.
* Перетаскивание **доступ** prefab в **панели иерархии**.

Далее нам нужно запустить совместно используемой службе. Только **одним ПК** в общей работы необходимо выполнить этот шаг.
* В Unity — в меню сверху рука об руку - выберите **меню совместное использование 240 HoloToolkit**.
* Выберите **запуска службы общего доступа к** элемента в раскрывающемся списке.
* Проверьте **частная сеть** и нажмите кнопку **разрешения доступа к** при появлении брандмауэра.
* Запишите IPv4-адрес, отображаемый в окне консоли службы совместного использования. Это же IP-адрес компьютера, на котором запущен под управлением службы.

Следуйте инструкциям **всех компьютеров под управлением** , присоединяются к опытом.
* В **иерархии**выберите **доступ** объекта.
* В **инспектор**на **общий доступ к рабочей области** компонента, изменение **адрес сервера** из «localhost» на IPv4-адрес машины, работающей SharingService.exe.
* В **иерархии** выберите **HologramCollection** объекта.
* В **инспектор** щелкните **добавить компонент** кнопки.
* В поле поиска введите **импорта экспорта привязки Manager**. Выберите результат поиска.
* В **панель проекта** перейдите к **сценариев** папки.
* Дважды щелкните **HologramPlacement** скрипт, чтобы открыть его в Visual Studio.
* Замените содержимое следующим кодом.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* В Unity, выберите **HologramCollection** в **панели иерархии**.
* В **панели Инспектора** щелкните **добавить компонент** кнопки.
* В меню, введите в поле поиска **диспетчер состояний приложения**. Выберите результат поиска.

**Развертывание и наслаждайтесь**
* Постройте проект для устройств HoloLens.
* Назначьте один HoloLens для развертывания на первый. Необходимо будет ждать привязки для отправки в службу до установки EnergyHub (это может занять около 30 – 60 секунд). До завершения отправки вашего жесты касания будет игнорироваться.
* После поместил EnergyHub ее расположение будет отправляться в службу и затем можно развернуть для других устройств HoloLens.
* Когда новый HoloLens сначала присоединится к сеансу, расположение EnergyHub может оказаться неправильной на этом устройстве. Тем не менее как только привязки и расположений EnergyHub были загружены из службы, EnergyHub должен перейти к новой, общего расположения. Если этого не происходит в пределах 30 – 60 секунд, пошаговые инструкции для которой был исходный HoloLens, при задании привязки, чтобы собрать дополнительные идеи среды. Если расположение по-прежнему не блокирует, повторное развертывание на устройстве.
* Когда устройства готовы и запуск приложения, найдите EnergyHub. Можно всем согласовать голограмма расположение и направление, в котором имеются текст?

## <a name="chapter-4---discovery"></a>Глава 4 — обнаружения

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Теперь все можно видеть же голограмма! Теперь давайте посмотрим, все еще подключены к веб-общего holographic. В этой главе мы будем захвата головной расположение и поворот все прочие устройства HoloLens в одном сеансе общего доступа.

### <a name="objectives"></a>Цели

* Обнаруживать друг друга в наш общий интерфейс.
* Выберите и совместно использовать аватар проигрывателя.
* Подключите аватар рядом с головах проигрывателя.

### <a name="instructions"></a>Инструкция

* В **панель проекта** перейдите к **голограммы** папки.
* Перетаскивание **PlayerAvatarStore** в **иерархии**.
* В **панель проекта** перейдите к **сценариев** папки.
* Дважды щелкните **AvatarSelector** скрипт, чтобы открыть его в Visual Studio.
* Замените содержимое следующим кодом.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* В **иерархии** выберите **HologramCollection** объекта.
* В **инспектор** щелкните **добавить компонент**.
* В поле поиска введите **локального диспетчера проигрывателя**. Выберите результат поиска.
* В **иерархии** выберите **HologramCollection** объекта.
* В **инспектор** щелкните **добавить компонент**.
* В поле поиска введите **диспетчера проигрывателя удаленного**. Выберите результат поиска.
* Откройте **HologramPlacement** скриптов в Visual Studio.
* Замените содержимое следующим кодом.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Откройте **AppStateManager** скриптов в Visual Studio.
* Замените содержимое следующим кодом.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Развертывание и наслаждайтесь**
* Построение и развертывание проекта на устройства HoloLens.
* Услышав эхо-тестирование звука, найдите меню выбора аватар и выберите аватар с жестом жест касания.
* Если вам не нужны в любой голограммы, точки, вокруг курсор света приводит к отключению другой цвет при вашей HoloLens взаимодействует со службой: инициализация (темно-фиолетовый), скачивание привязки (зеленый), Импорт и экспорт данных расположения (желтый), Отправка привязки (синий). Если точка света вокруг курсора находится цвет по умолчанию (сиреневый), вы будете готовы взаимодействовать с другими пользователями в текущем сеансе!
* Просмотрите другие пользователи подключены к вашей место — будет holographic робота над их плечо, сможет узнать и копируя их головной движения!

## <a name="chapter-5---placement"></a>Глава 5 - размещение

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

В этой главе мы предлагаем удается разместить на поверхностях реальных привязки. Мы будем использовать общий координаты для размещения этой привязки в средняя точка между всех опытом.

### <a name="objectives"></a>Цели

* Поместите голограммы на карте Пространственные, по положению головной игроков.

### <a name="instructions"></a>Инструкция

* В **панель проекта** перейдите к **голограммы** папки.
* Перетаскивание **CustomSpatialMapping** prefab на **иерархии**.
* В **панель проекта** перейдите к **сценариев** папки.
* Дважды щелкните **AppStateManager** скрипт, чтобы открыть его в Visual Studio.
* Замените содержимое следующим кодом.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* В **панель проекта** перейдите к **сценариев** папки.
* Дважды щелкните **HologramPlacement** скрипт, чтобы открыть его в Visual Studio.
* Замените содержимое следующим кодом.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Развертывание и наслаждайтесь**
* Построение и развертывание проекта на устройства HoloLens.
* Когда приложение будет готово, в круге, а также Обратите внимание на то, как EnergyHub отображается в центре всех пользователей.
* Коснитесь, чтобы поместить EnergyHub.
* Попробуйте голосовых команд «Сбросить Target», чтобы поднять EnergyHub и работают вместе как группа голограмма переместиться в новое расположение.

## <a name="chapter-6---real-world-physics"></a>Глава 6 - реальной физике

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

В этой главе мы добавим голограммы, отражаясь реальных поверхности. Смотрите модуля заполнения с проектами, запускаемого по вам и вашим друзьям!

### <a name="objectives"></a>Цели

* Запустите снаряды, отражаясь реальных поверхности.
* Используют снаряды, поэтому их можно было видеть других игроков.

### <a name="instructions"></a>Инструкция

* В **иерархии** выберите **HologramCollection** объекта.
* В **инспектор** щелкните **добавить компонент**.
* В поле поиска введите **Projectile запуска**. Выберите результат поиска.

**Развертывание и наслаждайтесь**
* Создавайте и развертывайте на устройства HoloLens.
* Когда приложение выполняется на всех устройствах, выполните жест касания для запуска projectile в реальном мире поверхности.
* См. в разделе, что происходит, когда ваш projectile конфликтует с другим игрока аватар!

## <a name="chapter-7---grand-finale"></a>Глава 7 - брошены общего итога

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

В этой главе мы будем Открывание это портал, который можно обнаружить только с помощью службы совместной работы.

### <a name="objectives"></a>Цели

* Совместная работа которых позволяет запустить достаточно летящими у привязки для выявления секретный портала!

### <a name="instructions"></a>Инструкция

* В **панель проекта** перейдите к **голограммы** папки.
* Перетаскивание **Underworld** ресурс как **потомком HologramCollection**.
* С помощью **HologramCollection** , щелкните **добавить компонент** кнопку **инспектор**.
* В меню, введите в поле поиска **ExplodeTarget**. Выберите результат поиска.
* С помощью **HologramCollection** выбранный из **иерархии** перетащите **EnergyHub** объект **целевой** в **Инспектор**.
* С помощью **HologramCollection** выбранный из **иерархии** перетащите **Underworld** объект **Underworld** в  **Инспектор**.

**Развертывание и наслаждайтесь**
* Создавайте и развертывайте на устройства HoloLens.
* При запуске приложения работе вместе, чтобы запустить летящими в EnergyHub.
* В открывшемся underworld запустите летящими в underworld роботов (попадание робота три раза для дополнительных интереса).
