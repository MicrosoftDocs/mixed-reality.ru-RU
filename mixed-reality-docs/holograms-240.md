---
title: MR-общий доступ 240 — несколько устройств HoloLens
description: Следуйте этому пошаговому руководству по созданию кода с помощью Unity, Visual Studio и HoloLens, чтобы получить сведения о голограммах общего доступа.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, общий доступ, сети, Academy, учебник
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522332"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR совместное использование 240: Несколько устройств HoloLens

Голограммы задаются в нашем мире по мере перемещения о месте в пространстве. HoloLens сохраняет голограммы на месте, используя различные [системы координат](coordinate-systems.md) для наблюдения за расположением и ориентацией объектов. При совместном использовании этих систем координат между устройствами мы можем создать общий интерфейс, который позволит нам принять участие в совместном мире Holographic.

В этом учебнике мы будем делать следующее:

* Настройте сеть для совместной работы.
* Делитесь голограммами на устройствах HoloLens.
* Знакомство с другими людьми в нашей общей жизни.
* Создайте общедоступную интерактивную среду, где вы можете ориентироваться на другие игроки и запустить снаряды.

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td>MR совместное использование 240: Несколько устройств HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>предварительные требования

* КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md) с доступом к Интернету.
* По крайней мере два устройства HoloLens [настроены для разработки](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) , необходимые для проекта. Требуется Unity 2017,2 или более поздней версии.
  * Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Отмена архивации файлов на Рабочий стол или другого места для удобства доступа. В качестве имени папки используйте **шаредхолограмс**.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Глава 1 — Холо World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

В этой главе мы создадим наш первый проект Unity и пошаговым процессом сборки и развертывания.

### <a name="objectives"></a>Цели

* Настройте Unity для разработки holographic приложений.
* Ознакомьтесь с голограммой!

### <a name="instructions"></a>Инструкция

* Запустите Unity.
* Нажмите кнопку **Открыть**.
* Введите Location в качестве ранее неархивированной папки **шаредхолограмс** .
* Выберите **имя проекта** и щелкните **выбрать папку**.
* В **иерархии**щелкните правой кнопкой мыши **основную камеру** и выберите **Удалить**.
* В папке **холотулкит-Shared-240/Prefabs/Camera** найдите **главную камеру** prefab.
* Перетащите **основную камеру** в **иерархию**.
* В **иерархии**щелкните **создать** и **создать пустой**.
* Щелкните правой кнопкой мыши новый **GameObject** и выберите команду **Переименовать**.
* Переименуйте GameObject в **холограмколлектион**.
* Выберите объект **холограмколлектион** в **иерархии**.
* В **инспекторе** задайте для параметра **Расположение преобразования** значение: **X 0, Y:-0,25, Z: 2**.
* В папке **голограмм** на **панели проект**найдите ресурс **енергихуб** .
* Перетащите объект **енергихуб** с **панели проект** в **иерархию** в качестве дочернего **элемента холограмколлектион**.
* Выберите **файл > сохранить сцену как...**
* Присвойте сцене имя **шаредхолограмс** и нажмите кнопку **сохранить**.
* Нажмите кнопку **воспроизвести** в Unity, чтобы просмотреть голограммы.
* Чтобы выйти из режима предварительного просмотра, нажмите кнопку **воспроизвести** еще раз.

**Экспорт проекта из Unity в Visual Studio**
* В Unity выберите **файл > параметры сборки**.
* Щелкните **Добавить открытые сцены** , чтобы добавить сцену.
* Выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.
* Задайте для **пакета SDK** значение **универсальное 10**.
* Присвойте **целевому устройству** значение **HoloLens** , а для **типа сборки UWP** — **D3D**.
* Проверьте **проекты C# Unity**.
* Щелкните **Сборка**.
* В открывшемся окне проводника создайте **новую папку** с именем App.
* Щелкните папку **приложения** одним щелчком мыши.
* Нажмите кнопку **выбрать папку**.
* После завершения Unity появится окно проводника.
* Откройте папку **приложения** .
* Откройте **шаредхолограмс. sln** , чтобы запустить Visual Studio.
* С помощью верхней панели инструментов в Visual Studio измените целевой объект с отладка на **выпуск** и с ARM на **x86**.
* Щелкните стрелку раскрывающегося списка рядом с пунктом локальный компьютер и выберите **удаленное устройство**.
    * Присвойте **адресу** имя или IP-адрес HoloLens. Если вы не знакомы с IP-адресом устройства, проверьте **параметры > сеть & интернет > дополнительные параметры** или спросите Кортану **"Привет, Кортана," мой IP-адрес ".**
    * Оставьте для параметра **режим проверки** подлинности значение **универсальное**.
    * Нажмите кнопку **выбрать** .
* Щелкните **отладка > начать без отладки** или нажмите клавиши **CTRL + F5**. Если вы впервые развертываете на устройстве, вам потребуется [связать его с Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
* Поставьте на HoloLens и найдите голограмму Енергихуб.

## <a name="chapter-2---interaction"></a>Глава 2 — взаимодействие

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

В этой главе мы будем взаимодействовать с нашими голограммами. Сначала мы добавим курсор для визуализации нашего [взгляда](gaze.md). Затем мы добавим [жесты](gestures.md) и будем использовать нашу руку, чтобы разместить наши голограммы в пространстве.

### <a name="objectives"></a>Цели

* Для управления курсором используйте ввод с помощью указателя.
* Используйте ввод жестов для взаимодействия с голограммами.

### <a name="instructions"></a>Инструкция

**Взгляд**
* На **панели Иерархия** выберите объект **холограмколлектион** .
* На **панели инспектора** нажмите кнопку **Добавить компонент** .
* В меню введите в поле поиска пункт **Менеджер**. Выберите результат поиска.
* В папке **HoloToolkit-Sharing-240\Prefabs\Input** найдите ресурс **cursor** .
* Перетащите в **иерархию**ресурс с **курсором** .

**Рисуйте**
* На **панели Иерархия** выберите объект **холограмколлектион** .
* Щелкните **Добавить компонент** и введите **Диспетчер жестов** в поле поиска. Выберите результат поиска.
* На **панели Иерархия**разверните узел **холограмколлектион**.
* Выберите дочерний объект **енергихуб** .
* На **панели инспектора** нажмите кнопку **Добавить компонент** .
* В меню введите текст в поле поиска с **голограммой**. Выберите результат поиска.
* Сохраните сцену, выбрав **файл > сохранить сцену**.

**Развертывание и наслаждайтесь**
* Выполните сборку и развертывание в HoloLens, следуя инструкциям из предыдущей главы.
* Когда приложение запустится на HoloLens, переместите заголовок и обратите внимание на то, как Енергихуб соответствует вашему взгляду.
* Обратите внимание на то, что курсор отображается при взгляде на голограмму, и меняется на светло-точечный, когда не облаками на голограмме.
* Выполните касание, чтобы разместить голограмму. В настоящее время в нашем проекте можно разместить голограмму только один раз (повторное развертывание, чтобы повторить попытку).

## <a name="chapter-3---shared-coordinates"></a>Глава 3. Общие координаты

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Приятно видеть голограммы и взаимодействовать с ними, но давайте дальше. Мы настроили наш первый общий интерфейс, который все может видеть одновременно.

### <a name="objectives"></a>Цели

* Настройте сеть для совместной работы.
* Создание общей контрольной точки.
* Совместное использование систем координат на разных устройствах.
* Все видят одну голограмму!

>[!NOTE]
>Для подключения приложения к серверу общего доступа необходимо объявить возможности **интернетклиентсервер** и **приватенетворкклиентсервер** . Это делается для тех, кто уже находится в голограммах 240, но не забывайте об этом с учетом собственных проектов.
>1. В редакторе Unity перейдите к параметрам проигрывателя, перейдя к разделу "изменение параметров проекта > > Player".
>2. Перейдите на вкладку "Магазин Windows".
>3. В разделе "Параметры публикации > возможности" проверьте возможность **интернетклиентсервер** и возможности **приватенетворкклиентсервер** .

### <a name="instructions"></a>Инструкция

* На **панели "проект** " перейдите в папку **HoloToolkit-Sharing-240\Prefabs\Sharing** .
* Перетащите prefab **доступа** на **панель Иерархия**.

Далее необходимо запустить службу общего доступа. Только **один компьютер** в общем интерфейсе должен выполнить этот шаг.
* В Unity — в меню верхнего уровня — выберите **меню холотулкит-Sharing-240**.
* В раскрывающемся списке выберите пункт **запустить службу общего доступа** .
* Проверьте параметр **частная сеть** и нажмите кнопку **Разрешить доступ** при появлении окна брандмауэра.
* Запишите IPv4-адрес, отображаемый в окне консоли службы общего доступа. Это тот же IP-адрес, что и у компьютера, на котором выполняется служба.

Следуйте остальным инструкциям на **всех ПК** , которые будут присоединяться к общему интерфейсу.
* В **иерархии**выберите объект **общего доступа** .
* В **инспекторе**в компоненте " **этап предоставления общего доступа** " измените **адрес сервера** с "localhost" на IPv4-адрес компьютера, на котором выполняется шарингсервице. exe.
* В **иерархии** выберите объект **холограмколлектион** .
* В **инспекторе** нажмите кнопку **Добавить компонент** .
* В поле поиска введите **Импорт экспорт привязки диспетчер**. Выберите результат поиска.
* На **панели проект** перейдите к папке **Scripts** .
* Дважды щелкните скрипт **холограмплацемент** , чтобы открыть его в Visual Studio.
* Замените содержимое на приведенный ниже код.

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

* Вернитесь в Unity, выберите **холограмколлектион** на **панели Иерархия**.
* На **панели инспектора** нажмите кнопку **Добавить компонент** .
* В меню введите в поле поиска **диспетчер состояний приложения**. Выберите результат поиска.

**Развертывание и наслаждайтесь**
* Создайте проект для устройств HoloLens.
* Назначьте один HoloLens для развертывания первым. Необходимо подождать, пока привязка будет отправлена в службу, прежде чем можно будет поместить Енергихуб (это может занять около 30-60 секунд). Пока передача не будет выполнена, жесты касания будут игнорироваться.
* После размещения Енергихуб его расположение загружается в службу, а затем можно выполнить развертывание на всех других устройствах HoloLens.
* Когда новый HoloLens впервые присоединяется к сеансу, расположение Енергихуб может быть неправильным на этом устройстве. Однако, как только расположения привязки и Енергихуб загружаются из службы, Енергихуб должен перейти к новому общему расположению. Если это не происходит в течение ~ 30-60 секунд, перед настройкой привязки для получения дополнительных сведений о среде следует проанализировать расположение исходного HoloLens. Если расположение по-прежнему не блокируется, выполните повторное развертывание на устройстве.
* Когда устройства готовы и запускают приложение, найдите Енергихуб. Можно ли принять все согласие на расположение голограммы и направление текста?

## <a name="chapter-4---discovery"></a>Глава 4. Обнаружение

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Теперь все могут видеть одну голограмму! Теперь давайте посмотрим все, кто еще подключен к нашему миру. В этой главе мы будем перехватить расположение и поворот всех других устройств HoloLens в одном сеансе совместного доступа.

### <a name="objectives"></a>Цели

* Найдите друг друга в нашем общем интерфейсе.
* Выберите и поделитесь с вами аватаром игрока.
* Вложите аватар игрока рядом с головами всех.

### <a name="instructions"></a>Инструкция

* На **панели проект** перейдите к папке **голограмм** .
* Перетащите **плайераватарсторе** в **иерархию**.
* На **панели проект** перейдите к папке **Scripts** .
* Дважды щелкните скрипт **аватарселектор** , чтобы открыть его в Visual Studio.
* Замените содержимое на приведенный ниже код.

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

* В **иерархии** выберите объект **холограмколлектион** .
* В **инспекторе** щелкните **Добавить компонент**.
* В поле поиска введите " **диспетчер локальных игроков**". Выберите результат поиска.
* В **иерархии** выберите объект **холограмколлектион** .
* В **инспекторе** щелкните **Добавить компонент**.
* В поле поиска введите **Remote Player Manager**. Выберите результат поиска.
* Откройте скрипт **холограмплацемент** в Visual Studio.
* Замените содержимое на приведенный ниже код.

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

* Откройте скрипт **аппстатеманажер** в Visual Studio.
* Замените содержимое на приведенный ниже код.

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
* Выполните сборку и развертывание проекта на устройствах HoloLens.
* Когда вы слышите звуковой сигнал, найдите меню выбора аватара и выберите аватар с помощью жеста касания.
* Если вы не видите ни одной голограммы, то, когда HoloLens взаимодействует со службой, световая точка вокруг курсора будет иметь другой цвет: инициализация (темно-фиолетовый), Загрузка привязки (зеленый цвет), импорт/экспорт данных о расположении (желтый цвет) Отправка привязки (синий цвет). Если точкой вокруг курсора является цвет по умолчанию (светло-сиреневый), вы готовы к взаимодействию с другими игроками в вашем сеансе!
* Взгляните на других пользователей, подключенных к своему модулю. в этом случае у вас будет один и тот же робот, а затем копируя свои головные движения!

## <a name="chapter-5---placement"></a>Глава 5. размещение

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

В этой главе привязку можно разместить на реальных поверхностях. Мы будем использовать общие координаты для размещения этой привязки в средней точке между всеми, подключенными к общему интерфейсу.

### <a name="objectives"></a>Цели

* Поместите голограммы на пространственной карте на основе головного расположения игроков.

### <a name="instructions"></a>Инструкция

* На **панели проект** перейдите к папке **голограмм** .
* Перетащите **кустомспатиалмаппинг** prefab на **иерархию**.
* На **панели проект** перейдите к папке **Scripts** .
* Дважды щелкните скрипт **аппстатеманажер** , чтобы открыть его в Visual Studio.
* Замените содержимое на приведенный ниже код.

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

* На **панели проект** перейдите к папке **Scripts** .
* Дважды щелкните скрипт **холограмплацемент** , чтобы открыть его в Visual Studio.
* Замените содержимое на приведенный ниже код.

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
* Выполните сборку и развертывание проекта на устройствах HoloLens.
* Когда приложение будет готово, наведите на окружность и обратите внимание на то, как Енергихуб отображается в центре всех.
* Коснитесь, чтобы поместить Енергихуб.
* Попробуйте выполнить команду "Сброс целевого объекта", чтобы выбрать Енергихуб резервное копирование и совместная работа в качестве группы для перемещения голограммы в новое место.

## <a name="chapter-6---real-world-physics"></a>Глава 6-вещественная физика

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

В этой главе мы добавим голограммы, которые возводят на реальные поверхности. Просматривайте свое пространство с помощью проектов, запущенных вами и вашими друзьями!

### <a name="objectives"></a>Цели

* Запустите снаряды, который перевернут на реальные поверхности.
* Предоставьте общий доступ к снаряды, чтобы другие игроки могли видеть их.

### <a name="instructions"></a>Инструкция

* В **иерархии** выберите объект **холограмколлектион** .
* В **инспекторе** щелкните **Добавить компонент**.
* В поле поиска введите **Прожектиле Launcher**. Выберите результат поиска.

**Развертывание и наслаждайтесь**
* Выполните сборку и развертывание на устройствах HoloLens.
* Когда приложение выполняется на всех устройствах, выполните воздушное касание, чтобы запустить прожектиле на реальных поверхностях.
* Узнайте, что происходит, когда прожектиле конфликтует с аватаром другого игрока!

## <a name="chapter-7---grand-finale"></a>Глава 7-Общий итог

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

В этой главе мы расскажем о портале, который может быть обнаружен только при совместной работе.

### <a name="objectives"></a>Цели

* Совместное использование позволяет запустить достаточно снаряды на привязке, чтобы обнаружить секретный портал.

### <a name="instructions"></a>Инструкция

* На **панели проект** перейдите к папке **голограмм** .
* Перетащите **этот ресурс** в качестве дочернего **для холограмколлектион**.
* Выбрав **холограмколлектион** , нажмите кнопку **Добавить компонент** в инспекторе.
* В меню введите **експлодетаржет**в поле поиска. Выберите результат поиска.
* Выбрав **холограмколлектион** , из **иерархии** перетащите объект **енергихуб** в целевое поле в **инспекторе**.
* Выбрав **холограмколлектион** , из **иерархии** перетащите объект «незаполненный **мир** » в поле «незаполненный **мир** » в **инспекторе**.

**Развертывание и наслаждайтесь**
* Выполните сборку и развертывание на устройствах HoloLens.
* После запуска приложения совместная работа для запуска снаряды на Енергихуб.
* Когда появится подсветка, запустите снаряды в подсвете роботов (нажмите робота три раза, чтобы получить дополнительные развлечения).
